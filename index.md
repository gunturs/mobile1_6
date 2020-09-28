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

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/gunturs/mobile1_6/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
