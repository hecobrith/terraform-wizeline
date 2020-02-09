# Terraform

crash course on wizeline queretaro for terraform and stuff autmated

Oscar Sosa
Miguel Oseguera
Eloy Vega

Wizeline crea una cultura de DevOps antes entre todo su personal, no se trata de tener un equipo de DevOps se trata de que todos tengan esa cultura.

**slides** at bit.ly/wzTerraform

**lab**: bit.lyWizeTFLab

Para los siguientes ejercicios usaremos Cloud9 que es un ambiente dentro aws para poder installar un ambiente por completo, tiene una IDE integrada y todo corre dentro de la red y consola preinstalada dentro de una instancia nano. Bastante conveniente para poder crearle un entorno de desarrollo a alguien ademas tiene funcionalidades de code share live coding, que puede ser algo bastante interesante para el trabajo y las horas. Echarle un ojo en el futuro a Cloud9 

## IaaS

Proceso de automatización de el creación de las nubes. Para llegar a ser agnostico de nubes es necesario tener terraform pues puedes hacer deploy multicloud etc.
HCL - se asemeja a un lenguaje de programadción mas usual. hashicorp configuration lenguaje, desarrollado en GO... por qué basicamente todos los lenguajes de autimización masiva esta en GO?
Plumi - investigar
saber el estado de la infraestructura es de las dificultades más grandes, ahí es donde terraform ayuda pues tiene una manera de crear el estado que se updatea cada vez. Providers, Resources, Data Sources, Variables, Modulos, Outputs, State son las caracterizitcas pricnipales de infraestructura.

dominar: Resource, Variable, Data Sources.
## Lesson 1

Terraform calcula un reosurce graph, entonces atrás sabe en un sistema de grafos mapear las dependencias para saber paralelamente como interactuan unos con otros.
### main commands

```bash
terraform init
terraform apply
terraform destroy
terraform fmt
terraform valdiate
terraform plan
terraform refresh
```

Resource blocks es de los conceptos mas importantes, son parte de la infraestructura que crea por lo tanto modularizar los blockes son lo que va haciendo que puedas compeljizar tu estructura.

*provider* se define todo lo que tenga que ver con el provedor<br>
*resource* define todo lo que tenga que ver dentro de un recurso

```bash
provider "aws" {
    region = "us-east-1
}

# el nombre del recurso es el segundo parametro de provider

resource "aws_instance" "web" {
    ami = "ami-wqeqwefqwef
    instance_type = "t2.micro"
}
```

Al ser un modulo se puede recrear el codigo y cada provider es único.

### variables

para poder hacer reutilizable y que realmente sea como codigo, es el termino de variables, simplenete son asignaciones key/value y puedes comenzar.

```bash
terraform plan \
-var 'mybar1=foo' \
-var 'myvar2=bar'
```

string, boolean, list, mapas, objetos etc... tambien tiene variables de ambiente en las que puede tomar automaticamente los valores ```-var -find``` encuentra el nombre de las variables y las asigna en el momento de correr las el plan

### Data Sources

Son proveidos por los mismos provedores jeje  por lo tanto para poder acceder a los datos ya creados por el provedor le pides cosas para poder re asignarlo.

generar outputs, de terraform para poder ligar servicios.

cloud trail  de amazon es un servicio para saber la conexion.}


### Dynamic nested blocks

Esta muy cabron investigalo, por que asignas aleatoriamente los tags dentro de un resource

### condicionales

Ocupa de un estilo de validación terniaria.

```bash 
var.env == "somthing" ? 1 : 0
```

