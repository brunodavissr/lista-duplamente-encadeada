#include <iostream>

using namespace std;

class No {
private:
	int valor;
	No *proximo;
	No *anterior;

public:
	No (): valor(0), proximo(nullptr), anterior(nullptr) {}
	
	void set_valor(int valor) {this->valor = valor;}
	void set_proximo(No *proximo) {this->proximo = proximo;}
	void set_anterior(No *anterior) {this->anterior = anterior;}
	
	int get_valor() {return this->valor;}
	No *get_proximo() {return this->proximo;}
	No *get_anterior() {return this->anterior;}
};

class Lista {
private:
	No *inicio;
	No *fim;
	int tamanho;
	    
public:
    Lista() : inicio(nullptr), fim(nullptr), tamanho(0) {}

    void inserir_no_inicio(int valor) {
        No *novo = new No;

    	novo->set_valor(valor);
        novo->set_proximo(this->inicio);
        if(this->tamanho == 0)
            this->fim = novo;
        else
        	this->inicio->set_anterior(novo);
        	
        this->inicio = novo;
        this->tamanho++;
    }
    
    void inserir_no_fim(int valor) {
    	No *novo = new No;

    	novo->set_valor(valor);
    	novo->set_anterior(this->fim);
        if(this->tamanho == 0)
        	this->inicio = novo;
        else
        	this->fim->set_proximo(novo);
		
        this->fim = novo;
        this->tamanho++;
	}
	
	void retirar_do_inicio() {
		No *no_inicio = this->inicio;
		
		if(this->tamanho == 0) {
			cout << "\nLista Vazia. Impossivel retirar elemento!\n";
			return;
		}
		else if(this->tamanho == 1)
			this->fim = nullptr;
		else
			this->inicio->get_proximo()->set_anterior(nullptr);
			
		this->inicio = this->inicio->get_proximo();
		delete no_inicio;
		this->tamanho--;
	}
	
	void retirar_do_meio(No *no) {
		no->get_proximo()->set_anterior(no->get_anterior());
		no->get_anterior()->set_proximo(no->get_proximo());
		delete no;
		this->tamanho--;
	}
	
	void retirar_do_fim() {
		No *no_fim = this->fim;
		
		if(this->tamanho == 0) {
			cout << "\nLista Vazia. Impossivel retirar elemento!\n";
			return;
		}
		else if(this->tamanho == 1)
			this->inicio = nullptr;
		else
			this->fim->get_anterior()->set_proximo(nullptr);
			
		this->fim = this->fim->get_anterior();
		delete no_fim;
		this->tamanho--;
	}
	
	void retirar_elemento(int valor) {
		for(No *i = this->inicio; i; i = i->get_proximo()) {
			if(i->get_valor() == valor) {
				if(i == this->inicio)
					retirar_do_inicio();
				else if(i == this->fim)
					retirar_do_fim();
				else
					retirar_do_meio(i);
				return;
			}
		}
		cout << "\nElemento nao presente na lista\n";
	}
	
	void retirar_iesimo_elemento(int i) {
		if(i >= this->tamanho || i < 0) {
			cout << "\nIndice nao existente. Impossivel retirar elemento\n";
			return;
		}
		No *no = this->inicio;
		for(; i; i--, no = no->get_proximo());
		if(no == this->inicio)
			retirar_do_inicio();
		else if(no == this->fim)
			retirar_do_fim();
		else
			retirar_do_meio(no);
	}
	
    void listar() {
    	cout << "\n";
        for(No *i = this->inicio; i; i = i->get_proximo())
        	cout << i->get_valor() << " ";
        cout << "\n";
    }

    ~Lista() {
        while (this->inicio) {
            retirar_do_inicio();
        }
    }
};

int main(void) {
    Lista lista;

    int opcao, valor;

    do {
        cout << "\n0 - Sair\n1 - Inserir no Inicio\n2 - Inserir no Fim\n3 - Retirar do Inicio\n4 - Retirar do Fim\n5 - Retirar Elementor\n6 - Retirar Iesimo Elemento\n7 - Listar:\n";
        cout << "\nEscolha uma opcao: ";
        cin >> opcao;
        
        switch(opcao) {
        	case 0:
        		break;
        	case 1:
        		cout << "\nDigite o valor que deseja inserir: ";
	            cin >> valor;
	            lista.inserir_no_inicio(valor);
	            break;
	        case 2:
	        	cout << "\nDigite o valor que deseja inserir: ";
	            cin >> valor;
	            lista.inserir_no_fim(valor);
	            break;
	        case 3:
	        	lista.retirar_do_inicio();
	        	break;
	        case 4:
	        	lista.retirar_do_fim();
	        	break;
	        case 5:
	        	cout << "\nDigite o valor que deseja retirar: ";
	        	cin >> valor;
	        	lista.retirar_elemento(valor);
	        	break;
	        case 6:
	        	cout << "\nDigite o indice que deseja retirar: ";
	        	cin >> valor;
	        	lista.retirar_iesimo_elemento(valor);
	        	break;
	        case 7:
	        	lista.listar();
	        	break;
	        default:
	        	cout << "\nOpcao Invalida\n";
	        	break;
		}
    }
	while (opcao != 0);

    return 0;
}
