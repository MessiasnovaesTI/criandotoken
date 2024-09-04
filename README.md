Desafio - Criação de Token ERC-20
Este repositório contém um desafio proposto pelo Instrutor Ricardo Zago, onde o objetivo é criar um Token ERC-20 do zero. O desafio envolve a configuração da Wallet Metamask, o uso da IDE REMIX, e o deploy do Token na blockchain.

Passos para o Desafio
1. Configuração da Metamask
Siga as instruções nos vídeos fornecidos para configurar a Metamask e adicionar um RPC customizado.

Vídeo 1: Configurando Metamask
Vídeo 2: Criando o seu Token
2. Desenvolvimento do Token
Utilize o código base fornecido no curso e siga os passos abaixo para implementar as funcionalidades do Token:

Balance Inquiry: Verifique o saldo de uma conta usando a função balanceOf.
Token Transfer: Permita a transferência de Tokens entre contas utilizando a função transfer.
Approval and TransferFrom: Implemente a aprovação para permitir que uma conta gaste Tokens de outra conta usando approve e transferFrom.
3. Implementação na IDE REMIX
Deploy do Token: Após fazer as alterações necessárias no código, use a IDE REMIX para compilar e fazer o deploy do seu Token.
Testando as Funcionalidades
Depois de fazer o deploy, você pode testar as seguintes funcionalidades diretamente na REMIX:

Verificar o saldo (balanceOf):

solidity
Copiar código
function balanceOf(address account) public view returns (uint256) {
    return balances[account];
}
Transferir Tokens (transfer):

solidity
Copiar código
function transfer(address recipient, uint256 amount) public returns (bool) {
    require(balances[msg.sender] >= amount, "Saldo insuficiente.");
    balances[msg.sender] -= amount;
    balances[recipient] += amount;
    emit Transfer(msg.sender, recipient, amount);
    return true;
}
Aprovar e Transferir Tokens (approve e transferFrom):

solidity
Copiar código
function approve(address spender, uint256 amount) public returns (bool) {
    allowed[msg.sender][spender] = amount;
    emit Approval(msg.sender, spender, amount);
    return true;
}

function transferFrom(address sender, address recipient, uint256 amount) public returns (bool) {
    require(balances[sender] >= amount, "Saldo insuficiente.");
    require(allowed[sender][msg.sender] >= amount, "Não autorizado.");
    balances[sender] -= amount;
    balances[recipient] += amount;
    allowed[sender][msg.sender] -= amount;
    emit Transfer(sender, recipient, amount);
    return true;
}
Considerações Finais
Este desafio é uma excelente oportunidade para aplicar conceitos de desenvolvimento em blockchain, especialmente no contexto da criação de Tokens ERC-20. Sinta-se à vontade para modificar e expandir o código conforme o necessário.

Divirta-se codando e boa sorte!

Este README fornece uma visão clara do desafio, juntamente com as instruções necessárias para implementar e testar as funcionalidades principais do Token.
