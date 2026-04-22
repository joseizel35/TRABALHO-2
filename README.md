lâmpada 
using System;

namespace Ex01_Lampada
{
    public class Lampada
    {
        private string _marca;
        private readonly string _tecnologia;
        private bool _ligada;
        private int _brilho;

        public string Marca => _marca;
        public string Tecnologia => _tecnologia;
        public bool Ligada => _ligada;
        public int Brilho => _brilho;

        public Lampada(string marca, string tecnologia)
        {
            _marca = marca;
            _tecnologia = tecnologia;
            _ligada = false;
            _brilho = 100;
        }

        public void Alternar()
        {
            _ligada = !_ligada;
        }

        public void AjustarBrilho(int novoBrilho)
        {
            if (!_ligada)
            {
                Console.WriteLine("A lâmpada precisa estar ligada.");
                return;
            }

            if (novoBrilho >= 0 && novoBrilho <= 100)
            {
                _brilho = novoBrilho;
            }
            else
            {
                Console.WriteLine("Brilho deve estar entre 0 e 100.");
            }
        }

        public override string ToString()
        {
            return $"Marca: {_marca}, Tecnologia: {_tecnologia}, Ligada: {_ligada}, Brilho: {_brilho}";
        }
    }
}



#cofre
using System;

namespace Ex02_Cofre
{
    public class Cofre
    {
        private string _dono;
        private string _senha;
        private bool _estaAberto;
        private int _tentativasErradas;

        public string Dono => _dono;
        public bool EstaAberto => _estaAberto;
        public int TentativasErradas => _tentativasErradas;

        public Cofre(string dono, string senhaInicial)
        {
            _dono = dono;
            _senha = senhaInicial;
            _estaAberto = false;
            _tentativasErradas = 0;
        }

        public void Abrir(string senhaInformada)
        {
            if (_tentativasErradas >= 3)
            {
                Console.WriteLine("Cofre bloqueado.");
                return;
            }

            if (senhaInformada == _senha)
            {
                _estaAberto = true;
                _tentativasErradas = 0;
                Console.WriteLine("Cofre aberto!");
            }
            else
            {
                _tentativasErradas++;
                Console.WriteLine("Senha incorreta.");
            }
        }

        public void Fechar()
        {
            _estaAberto = false;
        }

        public void AlterarSenha(string senhaAntiga, string novaSenha)
        {
            if (!_estaAberto)
            {
                Console.WriteLine("Cofre precisa estar aberto.");
                return;
            }

            if (senhaAntiga == _senha)
            {
                _senha = novaSenha;
                Console.WriteLine("Senha alterada com sucesso.");
            }
            else
            {
                Console.WriteLine("Senha antiga incorreta.");
            }
        }

        public override string ToString()
        {
            return $"Dono: {_dono}, Aberto: {_estaAberto}, Tentativas Erradas: {_tentativasErradas}";
        }
    }
}
