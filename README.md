# java-tp5

`Code de la classe EcritureObjet : `

```java
package personne;
import java.io.*;
public class EcritureObjet {
public static void main(String[] args) {
maison m1 = new maison("Monastir");
maison m2 = new maison("Sousse");
maison m3 = new maison("Tunis");
ObjectOutputStream fo;
try { fo = new ObjectOutputStream(new
FileOutputStream("c:/test/fObjet.data"));
fo.writeObject(m1);
fo.writeObject(m2);
fo.writeObject(m3);
fo.close(); }
catch (FileNotFoundException e) { e.printStackTrace(); }
catch (IOException e) { e.printStackTrace();
}
try { ObjectInputStream fol = new ObjectInputStream(new
FileInputStream("c:/test/fObjet.data"));
maison m4= (maison) fol.readObject();
maison m5= (maison) fol.readObject();
maison m6= (maison) fol.readObject();
System.out.println(m4 );
System.out.println(m5 );
System.out.println(m6 );
fol.close();
} catch (FileNotFoundException e) {
e.printStackTrace();
} catch (IOException e) {
e.printStackTrace();
} catch (ClassNotFoundException e) {e.printStackTrace();
}}
}
```


`Code de la classe Maison : `

```java
package personne;
import java.io.*;
public class maison implements Serializable{
public String adresse;
public maison(String adresse) {
this.adresse = adresse;
System.out.println("Creation maison ");
}
public String getAdresse(){ return adresse;}
public String toString(){ return " la maison est a l adresse: " +
adresse;}
}
```

`Code de la classe Personne : `

```java
package personne;
import java.io.*;
public class Personne implements Serializable {
public String nom = "Vide";
public maison m;
public Personne(String nom, String adresse) {
this.nom=nom;
m = new maison(adresse);
System.out.println("Creation Personne ");
}}
```
`Code de la classe PersonneMainEcriture : `
package personne;
import java.io.*;
import java.util.*;
public class PersonneMainEcriture {
public static void main(String[] args) {
Personne p1 = new Personne("Souguir","Nabeul");
Personne p2 = new Personne("Bannour","Sousse");Personne p3 = new Personne("ACHOUR",null);
maison m1 = new maison("Monastir");
ObjectOutputStream fo;
try { fo = new ObjectOutputStream(new
FileOutputStream("c:/test/fObjet.data"));
fo.writeObject(p1);
fo.writeObject(p2);
fo.writeObject(p3);
fo.writeObject(m1);
fo.writeObject(new java.util.Date());
final int[] tableau = { 1, 2, 3 };
fo.writeObject(tableau);
fo.writeUTF("ma chaine en UTF");
fo.writeLong(123456789);
fo.writeObject("ma chaine de caracteres");
fo.close(); }
catch (FileNotFoundException e) { e.printStackTrace(); }
catch (IOException e) { e.printStackTrace();
}
try { ObjectInputStream fol = new ObjectInputStream(new
FileInputStream("c:/test/fObjet.data"));
Personne p4 = (Personne)fol.readObject();
Personne p5 = (Personne)fol.readObject();
Personne p6 = (Personne)fol.readObject();
maison m2= (maison) fol.readObject();
Date d =(Date)fol.readObject();
System.out.println( "la date : " +d.toString());
int[] t = (int[])fol.readObject();
String s="";
for (int i=0;i<t.length;i++) s+=t[i];
System.out.println("le tableau est : " + s);
s= (String) fol.readUTF();
System.out.println("la chaine : " + s);
long x= (long)fol.readLong();
System.out.println("le nombre : " + x);
s= (String)fol.readObject();
System.out.println("la chaine est : " + s);System.out.println(p4);
System.out.println(p5 );
System.out.println(p6 );
System.out.println(m2 );
fol.close();
} catch (FileNotFoundException e) {
e.printStackTrace();
} catch (IOException e) {
e.printStackTrace();
} catch (ClassNotFoundException e) {
e.printStackTrace();
}}
}
```java

```


