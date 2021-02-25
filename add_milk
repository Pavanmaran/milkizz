import 'package:firebase_database/firebase_database.dart';
import 'package:flutter/material.dart';
import 'package:milkizz/contact.dart';

class AddContacts extends StatefulWidget {
var contact;
AddContacts(this.contact);
  @override
  _AddContactsState createState() => _AddContactsState();
}

class _AddContactsState extends State<AddContacts> {
  TextEditingController _nameController, _numberController, _desc2,link,name;
  String _typeSelected ='';
  String Uid = "76";

  DatabaseReference _ref;
  DatabaseReference lref;
  String lmilk;

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    _nameController = TextEditingController();
    _numberController = TextEditingController();
    _desc2 = TextEditingController();
    link = TextEditingController();
    name = TextEditingController();
    _ref = FirebaseDatabase.instance.reference().child('Milkizz');
    lref = FirebaseDatabase.instance.reference().child('Lvalues');
    lref.once().then((DataSnapshot snapshot){
      Map<dynamic,dynamic> values = snapshot.value;
      values.forEach((key, value) {
        lmilk = values['Lmilk'].toString();
        print(lmilk);

      });
    });

  }


  Widget _buildContactType(String title){

    return InkWell(

      child: Container(
        height: 40,
        width: 90,

        decoration: BoxDecoration(
          color: _typeSelected == title? Colors.green : Theme.of(context).accentColor,
          borderRadius: BorderRadius.circular(25),
        ),

        child: Center(child: Text(title, style: TextStyle(fontSize: 15,
            color: Colors.white),
        ),),),

      onTap: (){
        setState(() {
          _typeSelected = title;
        });
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Add Entry'),
      ),
      body: Container(
        margin: EdgeInsets.all(15),
        child:Expanded(
        child: SingleChildScrollView(
        child :Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            TextFormField(
              controller: _nameController,
              decoration: InputDecoration(
                hintText: 'ID',
                prefixIcon: Icon(
                  Icons.account_circle,
                  size: 30,
                ),
                fillColor: Colors.white,
                filled: true,
                contentPadding: EdgeInsets.all(15),
              ),
            ),
            SizedBox(height: 15),
            TextFormField(
              controller: name,
              decoration: InputDecoration(
                hintText: 'Enter User Name',
                fillColor: Colors.white,
                filled: true,
                contentPadding: EdgeInsets.all(15),
              ),
            ),
            SizedBox(height: 15),
            TextFormField(
              maxLines: 1,
              autofocus: false,
              //initialValue: 'yu',
              controller: TextEditingController(text:lmilk.toString()),
              decoration: InputDecoration(
                hintText: 'Milk',

                /* prefixIcon: Icon(
                  Icons.phone_iphone,
                  size: 30,
                ),  */
                fillColor: Colors.white,
                filled: true,
                 contentPadding: EdgeInsets.all(15),
              ),
            ),

            SizedBox(height: 20,),

            TextFormField(
              maxLines: 1,
              controller: _desc2,
              decoration: InputDecoration(
                hintText: 'Fat',
                /* prefixIcon: Icon(
                  Icons.phone_iphone,
                  size: 30,
                ), */
                fillColor: Colors.white,
                filled: true,
                contentPadding: EdgeInsets.all(15),
              ),
            ),

            SizedBox(height: 20,),

            TextFormField(
              maxLines: 1,
              controller: link,
              decoration: InputDecoration(
                hintText: 'LR',
                /* prefixIcon: Icon(
                  Icons.phone_iphone,
                  size: 30,
                ), */
                fillColor: Colors.white,
                filled: true,
                contentPadding: EdgeInsets.all(15),
              ),
            ),
            SizedBox(height: 15,),
            Container(
              height: 50,
              child: ListView(

                scrollDirection: Axis.horizontal,
                children: [
                  _buildContactType('Buffalo'),
                  SizedBox(width: 10,),

                  _buildContactType('Cow'),
                  SizedBox(width: 10,),

                ],
              ),
            ),
            SizedBox(height: 25,),
            Container(
              width: double.infinity,
              padding: EdgeInsets.symmetric(horizontal: 10),
              child: RaisedButton(child: Text('Save Data',style: TextStyle(
                fontSize: 20,
                color: Colors.white,
                fontWeight: FontWeight.w600,

              ),),
                onPressed: (){
                  saveContact();
                },

                color: Theme.of(context).primaryColor,
              ),
            )

          ],
        ),
      ),
    ),),);
  }
  String saveContact(){

    Uid = _nameController.text;
    String Milk = _numberController.text;
    String Fat = _desc2.text;
    String LR = link.text;
    String Name = name.text;

    Map<String,String> contact = {
      'Uid':Uid,
      'Milk': Milk,
      'Fat': Fat,
      'LR':LR,
      'Name':Name,
      'Category': _typeSelected,

    };
    return Uid;

    _ref.push().set(contact).then((value) {
      Navigator.pop(context);
    });


  }
}
