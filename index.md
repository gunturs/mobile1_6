# Formulir & Validation

Form merupakan fasilitas untuk menginput data, memiliki banyak bentuk tergantung bentuk data yang akan diinput. namun tidak hanya input data form juga dapat menginformasikan keakuratan data yang diinput seperti batasan data, kesesuaian data dan lain sebagainya.

>## Form Tanpa Validasi

Siapkan Class dengan jenis Stateful Widget 
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(App());
}

class App extends StatelessWidget {
  Widget build(context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: Text('Form Registrasi'),
        ),
        body: RegisterScreen(),
      ),
    );
  }
}

class RegisterScreen extends StatefulWidget {
  createState() {
    return RegisterScreenState();
  }
}

class RegisterScreenState extends State<RegisterScreen> {
  Widget build(context) {
    return Container(child: Text("Formulir"));
  }
}
```dart


Tambahkan komponen form pada class RegisterScreenState dengan widget yang diperlukan
dalam contoh ini akan diinput nama, email dan password

```dart
class RegisterScreenState extends State<RegisterScreen> {

  Widget build(context) {
    return Container(
      margin: EdgeInsets.all(20.0),
      child: Form( 
        child: Column( 
          
          children: [
            nameField(),
            emailField(),
            passwordField(),
            registerButton(),
          ],
        )
      ),
    );
  }

  Widget nameField() {
    //MEMBUAT TEXT INPUT 
    return TextFormField(
      decoration: InputDecoration(
        labelText: 'Nama Lengkap' 
      ),
    );
  }

  Widget emailField() {
    return TextFormField(
      keyboardType: TextInputType.emailAddress, 
      decoration: InputDecoration(
        labelText: 'Email',
        hintText: 'email@example.com',
      ),
    );
  }

  Widget passwordField() {
    return TextFormField(
      obscureText: true, 
      decoration: InputDecoration(
        labelText: 'Password',
        hintText: 'Enter Password',
      ),
    );
  }

  Widget registerButton() {
   
    return RaisedButton(
      color: Colors.blueAccent,
      onPressed: () {
      
      },
      child: Text('Daftar'), 
    );
  }
}
```dart



Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3


```

