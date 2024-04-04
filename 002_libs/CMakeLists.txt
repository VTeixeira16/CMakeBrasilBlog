cmake_minimum_required(VERSION 3.0)

#Comentarios em Cmake sao representados pela cerquilha

project(CriandoPrimeiraBiblioteca) #Nome do projeto

message("CMAKE_SOURCE_DIR: ${CMAKE_SOURCE_DIR}") #Exibe pasta onde esta o arquivo CMakeLists.txt
message("CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}") #Exibe pasta onde de onde o build ocorre

#Cria variaveis que serao usadas no decorrer do projeto
set(LIB_AMERICA_PATH    ${CMAKE_SOURCE_DIR}/libAmerica)

#GLOB feito para pegar arquivos das bibliotecas
file(GLOB LIB_AMERICA_HEADERS ${LIB_AMERICA_PATH}/inc/*.h)
file(GLOB LIB_AMERICA_SOURCES ${LIB_AMERICA_PATH}/src/*.c)

#Cria Biblioteca chamada libAmerica e vincula com os Headers e Sources
add_library(libAmerica ${LIB_AMERICA_HEADERS} ${LIB_AMERICA_SOURCES})

#Usado para especificar os diretórios de header.
#O primeiro parâmetro é o alvo (no caso, a biblioteca libAmerica)
#O segundo (e opcional) é o especificador de visibilidade. PRIVATE é usado apenas para o alvo atual e o PUBLIC permite o acesso para qualquer alvo.
#Após a definição (ou não) do especificador, temos os diretórios dos headers
target_include_directories(libAmerica PRIVATE ${LIB_AMERICA_PATH}/inc)
