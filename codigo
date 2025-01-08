import re

def valido(num_cpf):
    regex = r'^[0-9]{3}\.[0-9]{3}\.[0-9]{3}\-[0-9]{2}$'
    caracteres_separandos = list(num_cpf)
    return num_cpf, regex, caracteres_separandos

def verifica_regex(num_cpf, regex):
    if re.fullmatch(regex, num_cpf):
        print(f'CPF {num_cpf} está no formato correto.')
        return True
    else:
        print(f'CPF {num_cpf} está no formato incorreto.')
        return False

def inteiro_cpf(caracteres_separandos):
    cpf_inteiro = []
    for i in caracteres_separandos:
        try:
            num_int = int(i)
            cpf_inteiro.append(num_int)
        except ValueError:
            continue
    return cpf_inteiro

def pri_digito(cpf_parcial):
    resultado = 0
    for multiplicador, numero in enumerate(reversed(cpf_parcial), start=2):
        resultado += multiplicador * numero
    resto = resultado % 11
    primeiro_digito = 0 if resto < 2 else 11 - resto
    cpf_parcial.append(primeiro_digito)
    return cpf_parcial

def seg_digito(cpf_parcial):
    resultado = 0
    for multiplicador, numero in enumerate(reversed(cpf_parcial), start=2):
        resultado += multiplicador * numero
    resto = resultado % 11
    segundo_digito = 0 if resto < 2 else 11 - resto
    cpf_parcial.append(segundo_digito)
    return cpf_parcial

def validacao_digito(cpf_parcial, cpf_inteiro):
    if cpf_parcial[-2:] == cpf_inteiro[-2:]:
        print(f'O CPF é válido.')
    else:
        print(f'O CPF é inválido.')

def verifica_CPF(num_cpf):
    num_cpf, regex, caracteres_separandos = valido(num_cpf)
    if verifica_regex(num_cpf, regex):
        cpf_inteiro = inteiro_cpf(caracteres_separandos)
        cpf_parcial = cpf_inteiro[:9]
        cpf_parcial = pri_digito(cpf_parcial)
        cpf_parcial = seg_digito(cpf_parcial)
        validacao_digito(cpf_parcial, cpf_inteiro)

if __name__ == '__main__':
    num_cpf = input('Digite o CPF (formato XXX.XXX.XXX-XX): ')
    verifica_CPF(num_cpf)
