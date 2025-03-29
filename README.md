<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $para = "winduwalves@gmail.com";
    $assunto = "Novo Recrutamento - Alis Academy";
    
    $nome = $_POST["nome"];
    $idade = $_POST["idade"];
    $pais = $_POST["pais"];
    $discord = $_POST["discord"];
    $horario = $_POST["horario"];
    $categoria = isset($_POST["categoria"]) ? implode(", ", $_POST["categoria"]) : "";
    $motivo = $_POST["motivo"];

    $mensagem = "Nome/Nickname: $nome\n";
    $mensagem .= "Idade: $idade\n";
    $mensagem .= "País/Cidade: $pais\n";
    $mensagem .= "Discord: $discord\n";
    $mensagem .= "Disponibilidade de Horário: $horario\n";
    $mensagem .= "Categoria de Interesse: $categoria\n";
    $mensagem .= "Motivo para entrar: $motivo\n";

    $headers = "From: noreply@teusite.com\r\n";
    $headers .= "Reply-To: $para\r\n";

    if (mail($para, $assunto, $mensagem, $headers)) {
        echo "Formulário enviado com sucesso!";
    } else {
        echo "Erro ao enviar o formulário.";
    }
} else {
    echo "Acesso inválido!";
}
?>
