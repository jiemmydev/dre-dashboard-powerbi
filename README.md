# Financeiro Empresarial

Aplicativo de gestão financeira empresarial feito em Python, Kivy e SQLite,
com lançamentos categorizados, DRE gerencial mensal e indicadores financeiros.

## Recursos

- Registro local de receitas e despesas com categoria e subcategoria.
- Classificação automática do tipo de lançamento pela subcategoria.
- DRE gerencial mensal com Receita Líquida, Lucro Bruto, EBITDA, Lucro
  Operacional e Lucro/Prejuízo Líquido.
- KPIs: margens bruta, EBITDA e líquida; pesos de CMV, pessoal e ocupação sobre
  Receita Líquida.
- Persistência SQLite local e migração de dados do formato anterior.
- Interface Kivy adaptável a telas verticais e navegação entre três telas.

> A DRE é gerencial e simplificada. Não substitui demonstrações contábeis ou
> fiscais nem representa aconselhamento contábil.

## Executar no Windows

Requer Python 3.10 ou superior. No PowerShell, na pasta do projeto:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python main.py
```

O banco é salvo no diretório privado de dados do Kivy. Os testes do motor
financeiro podem ser executados sem iniciar a interface:

```powershell
python -m unittest discover -s tests -v
```

## Gerar APK Android

Buildozer precisa de Linux. Em Windows, use WSL 2 com Ubuntu e copie apenas os
arquivos do app (`app.py`, `finance_core.py`, `main.py`, `requirements.txt`,
`buildozer.spec`, `README.md`, `GUIA_ANDROID.md` e `tests/`) para uma pasta no
sistema de arquivos Linux do WSL. Instruções completas de dependências e
compilação estão em [GUIA_ANDROID.md](./GUIA_ANDROID.md).

## Estrutura

- `main.py`: ponto de entrada para execução e Buildozer.
- `app.py`: interface e ciclo de vida Kivy.
- `finance_core.py`: regras financeiras, percentuais e persistência SQLite.
- `tests/`: testes unitários de cálculos, dados e migração.
- `buildozer.spec`: configuração de empacotamento Android.

O Git ignore exclui o ambiente virtual, bancos locais, arquivos gerados e as
pastas de cursos/planilhas que também existem neste workspace.
