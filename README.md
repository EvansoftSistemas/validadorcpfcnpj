
// Created by Evandro Albuquerque Bezerra on 18/07/17.



// Classe de validação de números de CPF e CNPJ

// Esta classe retorna um valor booleano


class Validar_CPF_CNPJ {

   
// Método de verificação e validação.

// Verifica se a entrada é de 11 ou 14 caracteres numéricos.

// Caso seja CPF ou CNPJ, faz o teste de validação correspondente.

// @param numero (String)

// Return boolean

    boolean valida_cpf_cnpj(String numero){

        // Verifica se é apenas números 
        if(numero =~ /[0-9]+/){
            
	    // Verifica se a entrada é um CPF
            if(numero.length()==11) {
                return valido_cpf(numero)
            }

            // Verifica se a entrada é um CNPJ
            if(numero.length()==14){
                return valido_cnpj(numero)
            }
        }
	// Retorna falso se a entrada não for de caracteres numéricos
        else{
            return false
        }
    }


// Método de Validação do CPF

// @param cpf (String)

// Return boolean

    boolean valido_cpf(String cpf){

        // Armazena os dígitos do CPF
        int dig1 = 0
        int dig2 = 0

        // Verifica se os números do CPF são todos iguais. Os dígitos não podem ser todos iguais.
        if(cpf =~ /(\d)\1{10}/){
            return false
        }
        else {

            // Cálculo de validação do dígito 1
            dig1 += 10 * cpf[0].toInteger()
            dig1 += 9 * cpf[1].toInteger()
            dig1 += 8 * cpf[2].toInteger()
            dig1 += 7 * cpf[3].toInteger()
            dig1 += 6 * cpf[4].toInteger()
            dig1 += 5 * cpf[5].toInteger()
            dig1 += 4 * cpf[6].toInteger()
            dig1 += 3 * cpf[7].toInteger()
            dig1 += 2 * cpf[8].toInteger()

            int resdig1 = 11 - (dig1 % 11)
            if(resdig1 == 10 || resdig1 == 11){
                dig1 = 0
            }else {
                dig1 = 11 - (dig1 % 11)
            }

            // Cálculo de validação do dígito 2
            dig2 += 11 * cpf[0].toInteger()
            dig2 += 10 * cpf[1].toInteger()
            dig2 += 9 * cpf[2].toInteger()
            dig2 += 8 * cpf[3].toInteger()
            dig2 += 7 * cpf[4].toInteger()
            dig2 += 6 * cpf[5].toInteger()
            dig2 += 5 * cpf[6].toInteger()
            dig2 += 4 * cpf[7].toInteger()
            dig2 += 3 * cpf[8].toInteger()
            dig2 += 2 * cpf[9].toInteger()

            int resdig2 = 11 - (dig2 % 11)
            if(resdig2 == 10 || resdig2 == 11)            {
                dig2 = 0
            }else {
                dig2 = 11 - (dig2 % 11)
            }

            // Transforma os dígitos do CPF em String e concatena
            String digitos1 = dig1.toString() + dig2.toString()

            // Concatena os dígitos do CPF 
            String digitos2 = cpf[9] + cpf[10]

            // Compara se os dígitos os calculados e os informados são idênticos
            if (digitos1 == digitos2) {
                return true
            } else {
                return false
            }
        }
    }


// Método de Validação do CNPJ

// @param cnpj (String)

// Return boolean

    boolean valido_cnpj(String cnpj){

        // Armazena os dígitos do CNPJ
        int dig1 = 0
        int dig2 = 0

        // Verifica se os números do CNPJ são todos iguais. Os dígitos não podem ser todos iguais.
        if(cnpj =~ /(\d)\1{13}/){
            return false
        }
        else {

            // Cálculo de validação do dígito 1
            dig1 += 5 * cnpj[0].toInteger()
            dig1 += 4 * cnpj[1].toInteger()
            dig1 += 3 * cnpj[2].toInteger()
            dig1 += 2 * cnpj[3].toInteger()
            dig1 += 9 * cnpj[4].toInteger()
            dig1 += 8 * cnpj[5].toInteger()
            dig1 += 7 * cnpj[6].toInteger()
            dig1 += 6 * cnpj[7].toInteger()
            dig1 += 5 * cnpj[8].toInteger()
            dig1 += 4 * cnpj[9].toInteger()
            dig1 += 3 * cnpj[10].toInteger()
            dig1 += 2 * cnpj[11].toInteger()

            int resdig1 = (dig1 % 11)
            if (resdig1 == 0 || resdig1 == 1){
                dig1 = 0
            }else {
                dig1 = 11- (dig1 % 11)
            }

            // Cálculo de validação do dígito 2
            dig2 += 6 * cnpj[0].toInteger()
            dig2 += 5 * cnpj[1].toInteger()
            dig2 += 4 * cnpj[2].toInteger()
            dig2 += 3 * cnpj[3].toInteger()
            dig2 += 2 * cnpj[4].toInteger()
            dig2 += 9 * cnpj[5].toInteger()
            dig2 += 8 * cnpj[6].toInteger()
            dig2 += 7 * cnpj[7].toInteger()
            dig2 += 6 * cnpj[8].toInteger()
            dig2 += 5 * cnpj[9].toInteger()
            dig2 += 4 * cnpj[10].toInteger()
            dig2 += 3 * cnpj[11].toInteger()
            dig2 += 2 * cnpj[12].toInteger()

            int resdig2 = (dig2 % 11)
            if (resdig2 == 0 || resdig2 == 1){
                dig2 = 0
            }else {
                dig2 = 11 - (dig2 % 11)
            }

            // Transforma os dígitos do CNPJ em String e concatena
            String digitos1 = dig1.toString() + dig2.toString()

            // Concatena os dígitos do CNPJ
            String digitos2 = cnpj[12] + cnpj[13]

            // Compara se os dígitos os calculados e os informados são idênticos
            if (digitos1 == digitos2) {
                return true
            } else {
                return false
            }
        }
    }
}

