###### UNIVERSIDAD DE INVESTIGACION Y DESARROLLO - UDI
###### AUTORES: Laura Daniela Pinzón Lizarazo y Anahis Enith Rodríguez Suescún
###### DOCENTE: Michael Sneider Puentes Palacio
###### GRUPO: 4L  

###### PROYECTO DE PROGRAMACIÓN SEGUNDO CORTE

#### Contenido

1. [Lenguaje utilizado.](#lenguaje-utilizado)
2. [¿Cómo instalar el programa?](#cómo-instalar-el-programa)
3. [Herramientas utilizadas.](#herramientas-utilizadas)
4. [Video ilustrativo.](#video)

#### Lenguaje utilizado.
Este proyecto está desarrollado en lenguaje C# en Visual Studio 2019.

#### ¿Cómo instalar el programa?

Para la instalación del software se deben seguir los siguientes pasos.

1. Tenemos la visualización del programa en la pantalla.

   ![Ima1](https://user-images.githubusercontent.com/62104463/81245215-0eabbd00-8fda-11ea-9108-aef2f1284514.png)
 
2. Damos clic en ***`Clone or download`*** y seleccionamos la opción ***`Download ZIP`*** para poder descargar el software.

   ![Ima2](https://user-images.githubusercontent.com/62104463/81244963-5ed64f80-8fd9-11ea-92ba-527fb403e604.png)  ![Ima3](https://user-images.githubusercontent.com/62104463/81245501-c50fa200-8fda-11ea-8326-578b82172c6b.png)

3. Al descargarlo, nos dirigimos al lugar donde quedó descargado el software y descomprimimos el archivo. Al tener ya descomprimido el archivo, abrimos la carpeta y descomprimimos también los dos archivos que aparecen comprimidos.

   ![Ima4](https://user-images.githubusercontent.com/62104463/81246022-2126f600-8fdc-11ea-9fd0-c185e22c5c34.png) ![Ima5](https://user-images.githubusercontent.com/62104463/81245843-acec5280-8fdb-11ea-90c4-71ec460df3dd.png)

4. Por último, abrimos el archivo que dice **ProyectoCorte1** .

   ![Ima6](https://user-images.githubusercontent.com/62104463/81246486-60a21200-8fdd-11ea-8a9f-9367f035fb2d.png)

   ```
   Aquí una explicación detallada: https://youtu.be/3I9m5sT4Q6Y
   ```
   [![VideoInstalar](https://j.gifs.com/YW9AAO.gif)](https://youtu.be/3I9m5sT4Q6Y)
   
#### Herramientas utilizadas.
 Las herramientas utilizadas en el proyecto se explicarán acontinuación:

 En la parte del diseño principal utilizamos herramientas como label, textBox, comboBox, button, panel y colorDialog. Estás, a su vez cumplian con algunos requisitos pedidos para una mejor visualización del programa.
 
 Primero, asignamos a cada label su respectivo textBox o comboBox, esto para saber que datos y tipo de datos debemos ingresar en cada uno. 
 
 ![Ima7](https://user-images.githubusercontent.com/62104463/81249607-aa422b00-8fe4-11ea-965e-415cee8f8b25.png)
 
 Segundo, agrupamos las diferentes herramientas en su respectivo groupBox, el título de los groupBox se encuentra centrado por lo que para que quede de esa forma nos basamos del código encontrado en esta [página](https://stackoverflow.com/questions/31827366/how-to-make-group-box-text-alignment-center-in-win-forms).
 
 ![Ima8](https://user-images.githubusercontent.com/62104463/81250214-022d6180-8fe6-11ea-9b79-2fc969207131.png)
 
 Tercero, cada uno de los button que aparecen en el diseño tienen una configuración diferente. Por ejemplo, el button llamado ***`Agregar`***, permite que al ingresar todos los datos correspondientes se guarden pero si no se ha llenado ningún dato deberá mostrar un mensaje que diga ***`Por favor, llene todos los campos`***.
 
 ![Ima9](https://user-images.githubusercontent.com/62104463/81250944-cd220e80-8fe7-11ea-819f-c93c1a7cb6d1.PNG)
 
 Para lograr esto, usamos el siguiente código.
 ```
 if (TB_NombreSerie.Text!="" || TB_NumeroTemp.Text!="" || TB_NumeroCap.Text!="" || TB_GeneroSerie.Text.ToUpper()!=""|| comboBox1.Text!="")
 {
      //Código completo
 }else
 {
      MessageBox.Show(Res.mjsAdvertencia,Res.mjsError, MessageBoxButtons.OK, MessageBoxIcon.Error);
 }
 ```
 En caso de que queramos cambiar el color al diseño principal, damos clic en el button ***`Color`***, este nos mostrará una paleta de colores, donde podremos escoger el color que deseemos.
 
![Ima10](https://user-images.githubusercontent.com/62104463/81253536-67855080-8fee-11ea-9a03-cd146c2ffd9e.png) ![Ima11](https://user-images.githubusercontent.com/62104463/81253674-b337fa00-8fee-11ea-87bd-62aea37e9982.png)

 ```
 ColorDialog color = new ColorDialog();
 color.ShowDialog();
 this.BackColor = color.Color;
 ```
 
Por otra parte, algunos textBox y el comboBox, tienen una condición especial:

1. Para los textBox que reciben datos numéricos, estos solo podran ser de tipo int, si llegado el caso se ingresa algún dato tipo string, saldrá el siguiente mensaje ***`Sólo se permiten números`***. Esto lo hicimos con ayuda del evento *KeyPress* y dentro de él llamamos a una clase que realizamos, la cual nos permitía hacer las validaciones de si era un dígito. 

Un ejemplo es el siguiente:

  ```
  private void TB_NumeroTemp_KeyPress(object sender, KeyPressEventArgs e)
  {
     cs_Validaciones.SoloNumeros(e);
  }
  ```
  ![Ima12](https://user-images.githubusercontent.com/62104463/81254688-71f51980-8ff1-11ea-9684-b12e7193e87d.PNG)
  
 2. Si queremos que el texto digitado se convierta todo en mayúscula, usamos:
 
  ```
  private void TB_GeneroSerie_Leave(object sender, EventArgs e)
  {
     TB_GeneroSerie.Text = TB_GeneroSerie.Text.ToUpper();
  }
  ```
  ![Ima13](https://user-images.githubusercontent.com/62104463/81255070-58080680-8ff2-11ea-9bb3-7036b825a414.PNG)
  
 3. Y si en el comboBox queremos que los datos ingresados se guarden y se muestren en una lista.
 
  ```
  comboBox1.Items.Add(comboBox1.Text);
  comboBox1.Text = " ";
  ```
  
 Continuando con las herramientas utilizadas, tenemos el *panel* que recibe todos los datos del *userControl*. Este userControl recibe los datos de un segundo formulario, nuestro primer formulario es donde ingresamos por primera vez los datos, en nuestro caso (**los datos de una serie**), y nuestro segundo formulario muestra los mismos datos ingresados pero con la opción de modificar algún dato que queramos y en este formulario también utilizamos una herramienta adicional que es un *checkBox*.
 
 ![Ima14](https://user-images.githubusercontent.com/62104463/81256347-d7e3a000-8ff5-11ea-917e-f2adaab52e92.png)    ![Ima15](https://user-images.githubusercontent.com/62104463/81256523-62c49a80-8ff6-11ea-918a-0019f0d19107.png)
 ![Ima16](https://user-images.githubusercontent.com/62104463/81627179-3c6e7880-93c3-11ea-9859-67305849e9fb.png)

   ```
   Este parte de código es para agregar los datos al userControl.
   ```
   ```
   UserControl1 miUC = new UserControl1(TB_NombreSerie.Text, misRegistros, contador,this);
   panel1.Controls.Add(miUC);
   miUC.Location = new System.Drawing.Point(9, valor);
   valor = valor + miUC.Size.Height;
   TodoUC.Add(miUC);
   ```
   
 Otras de las herramientas utilizadas se encuentran en nuestras DLL.
 
 En nuestra primera DLL llamada *DLL_Numero* la utilizamos para calcular la raiz de un número. Al ingresar un número de varios dígitos, se suman cada uno de los dígitos hasta que quede solo un dígito.
 
  ```
  int nume = int.Parse(numero);
  int acum = 0;
  do
  {
     acum = 0;
     while (nume > 0)
  {
     var cifra = nume % 10;
     acum += cifra;
     nume = nume / 10;
  }
     nume = acum;
  } 
  while (acum > 10);
  return acum;
  ```
  ![Ima17](https://user-images.githubusercontent.com/62104463/81365398-9ca4a800-90ad-11ea-8687-7fb3a1477b07.png)
  
 Y en nuestra segunda DLL llamada *DLL_Graficador* permite graficar los datos (*Nombre de la serie* y *Número de temporadas*) en un **chart**. Al actualizar alguno de los datos del segundo formulario que están en la gráfica, los datos en el *chart* también se modifican.
 ```
 Agregar datos al chart
 ```
 ```
 this.chart1.Series["Nombre de la serie"].Points.AddXY(nombreSerie,numTemporadas);
 ```
 ![Ima18](https://user-images.githubusercontent.com/62104463/81627507-f665e480-93c3-11ea-8ad5-add51a2d8da9.png)
 
 Además, en nuestro software utilizamos la herencia en diferentes formularios.Como bien sabemos la herencia se identifica con **:** . Lo que hicimos fue crear varios formularios llamados *h_about*,*h_informacion*,*h_llenarDatos* y *h_formularioBase* (este será el que heredará todas sus características a los demás formularios).
 
 En el formulario *h_formularioBase*, escribimos este código:
 
 ```
 DialogResult RTA = MessageBox.Show(Res.mjs_Information, Res.mjs_Advertencia, MessageBoxButtons.YesNo, MessageBoxIcon.Question);
 if (RTA == DialogResult.Yes)
 {
 h_about F = new h_about(base.BackColor);
 F.Show();
 }
 ```
 Este código, si lo queremos tener en los otros formularios, ya no será necesario copiarlo en cada uno de ellos porque al momento de hacer ***herencia***, todos los formularios a los que el *h_formularioBase* haya hecho herencia, tendrán las características de ese formulario.
 
 ```
 h_llenardatos : h_formularioBase   //  h_informacion : h_formularioBase  //  h_about : h_formularioBase
 ```
 
 El formulario *h_about*, tendrá una característica adicional, porque nos permitirá escribir algo en un textBox.
 
 ![Ima19](https://user-images.githubusercontent.com/62104463/81629497-e3a1de80-93c8-11ea-9be0-3db5b6b3e10c.png)    ![Ima20](https://user-images.githubusercontent.com/62104463/81629704-6034bd00-93c9-11ea-9416-9008b5a7d456.png)  
 ![Ima21](https://user-images.githubusercontent.com/62104463/81629842-c02b6380-93c9-11ea-9690-7c1e519a22ee.png)    ![Ima22](https://user-images.githubusercontent.com/62104463/81630162-7a22cf80-93ca-11ea-8e8a-43ebfcc49764.png)

  
 Y para tener acceso directo a estos formularios desde el diseño principal, en nuestro diseño principal agregamos unos button correspondiente a los formularios.
 
 ![Ima23](https://user-images.githubusercontent.com/62104463/81628047-38dbf100-93c5-11ea-8547-963e1b0abe3e.png)
 
 Finalmente, nuestro diseño principal tiene la opción de cambiar de idioma cada uno de los label, textBox, button y message. Los idiomas escogidos fueron *español*, *inglés* y *francés*.
 
 ![Ima24](https://user-images.githubusercontent.com/62104463/81628489-69705a80-93c6-11ea-8d86-f553fb2c85ad.png)  ![Ima25](https://user-images.githubusercontent.com/62104463/81628521-8147de80-93c6-11ea-9f77-4a3cd7bdbdff.png)
  ![Ima26](https://user-images.githubusercontent.com/62104463/81628568-9de41680-93c6-11ea-8a77-d979608a0a50.png)

```
NOTA: 
Hay que tener en cuenta que para hacer el cambio de idioma, es necesario hacer un resource tanto en las dll como en el proyecto, para cada idioma se hace un resource diferente. En cada *resource* colocamos todos las herramientas que queramos que se aplique el cambio de idioma y el texto que va a tener en cada idioma.
```
Para realizar el cambio de idioma usamos: 

```
if (CB_Idioma.SelectedIndex == 1)
{
//Idioma inglés.
Thread.CurrentThread.CurrentUICulture = new CultureInfo("en-US");
Renombrar("en-US");
}
if(CB_Idioma.SelectedIndex == 2)
{
//Idioma francés.
Thread.CurrentThread.CurrentUICulture = new CultureInfo("fr-FR");
Renombrar("fr-FR");
}
if (CB_Idioma.SelectedIndex == 0)
{
//Idioma por defecto español.
Thread.CurrentThread.CurrentUICulture = new CultureInfo("es-CO");
Renombrar("es-CO");
}
```

#### Video.

```
   Demostración del software: https://www.youtube.com/watch?v=hcsmGwW2GPs
```
[![VideoFuncionalidad](https://j.gifs.com/jZ9mmY.gif)](https://www.youtube.com/watch?v=hcsmGwW2GPs)
