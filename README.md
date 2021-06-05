# Blog-app

Dokumentacja

1.	CHARAKTERYSTYKA
 Wizjonerzy- Magdalena Rulska, Marta Pietrzak, Szymon Musiołowski
a. Nazwa skrócona- Blog app
b. Nazwa pełna- Aplikacja Android wykorzystująca Firebase
c. Cele- nauka oraz poszerzenie wiedzy dotyczącej firebase w aplikacjach na platformę  Android; zagłębienie wiedzy dotyczącej programowania w języku Java w programie Android Studio, poszerzenie wiedzy dotyczącej działania programu Android Studio


2.	PRAWA AUTORSKIE
a)	Wizjonerzy- Magdalena Rulska, Marta Pietrzak, Szymon Musiołowski
b)	Autorzy- Magdalena Rulska, Marta Pietrzak, Szymon Musiołowski

3.	SPECYFIKACJA WYMAGAŃ- Marta Pietrzak
WYMAGANIA FUNKCJONALNE:
•	Okno logowania- wymagane
•	Okno logowania- pole „Wpisz email”- wymagane
•	Okno logowania- pole „Wpisz hasło”- wymagane
•	Okno logowania- „Zapomniałem hasła”- wymagane
•	Okno logowania- Zarejestruj się- wymagane
•	Okno logowania- przycisk- zaloguj się- wymagane
•	Okno zalogowane- rozwijane menu- opcja „Wyloguj się”- wymagane
•	Okno rejestracji- pole „Wpisz email”- wymagane
•	Okno rejestracji- pole „Wpisz hasło”- wymagane
•	Okno rejestracji- przycisk- zarejestruj się- wymagane
•	Okno rejestracji- pole- masz już konto?- wymagane
•	Okno postowania- pole „Tytuł”- wymagane
Okno postowania- pole „Wyświetlanie obrazów”- wymagane
•	Okno postowania- przycisk- załaduj- wymagane


WYMAGANIA NIEFUNKCJONALNE

•	Android- aplikacja napisana w Androidzie- wymagane
•	Prosty interfejs dla użytkownika- przydatne
•	Wersja polska- opcjonalne
•	Baza danych Firebase- wymagane


4.	Architektura systemu i oprogramowania

Architektura rozwoju:

Android 11.0
Java 8
Firebase - https://console.firebase.google.com/u/0/?hl=pl

Architektura uruchomieniowa:

Android 
Java JDK
Urządzenie mobilne z oprogramowaniem Android



5.WYGLĄD APLIKACJI

  ![image](https://user-images.githubusercontent.com/85177651/120908197-34394900-c668-11eb-9512-60bd4f436ce5.png)
Okno LOGOWANIE- możliwość zalogowania się do aplikacji poprzez wpisanie e-mail oraz hasła; możliwość wyboru opcji zarejestrowania się, możliwość przejścia do następnego okna aplikacji poprzez wciśnięcie przycisku „Zaloguj się”; brak możliwości przejścia do następnego okna bez wpisania e-mail oraz hasła ( gdy e-mail/hasło nie zostanie wpisane wyświetla się komunikat „Email/Hasło jest wymagane”; w przypadku poprawnie wpisanych danych wyświetlany jest komunikat „Sukces”, a w przypadku błędnie wpisanych danych wyświetlany jest komunikat „Błędnie wpisany login lub hasło”





Fragment kodu przedstawiający poprawność/niepoprawność zalogowania:













Fragment kodu przedstawiający wymóg:












Fragment kodu pokazujący okno „Proszę czekać” wyświetlany po naciśnięciu przycisku „Zaloguj się”
private void Login(String email, String password) {
    progressDialog.setTitle("Proszę Czekać...");
    progressDialog.show();











                                           Okno REJESTRACJA- możliwość zarejestrowania konta poprzez wpisanie 
 e-mail oraz hasła; możliwość zarejestrowania konta poprzez przycisk „zarejestruj się”; po zarejestrowaniu konta dane użytkownika przesyłane są do połączonej z nim bazy danych; możliwość ponownego przejścia do okna „Zaloguj się”

Aplikacja sprawdza również czy dane użytkownika sa już wpisane w bazie danych za pomocą fragmentu kodu:

 
 Okno DODAJ POST- możliwość wpisania tytułu publikowanego wpisu; możliwość dodania zdjęcia do publikowanego wpisu; możliwośc zapisania wpisu za pomocą przycisku załaduj (widoczny w kodzie ponieżej) 

Fragment kodu przedstawiający wygląd okna:
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".AddpostActivity">

    <LinearLayout
        android:orientation="vertical"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <EditText
            android:id="@+id/title"
            android:inputType="textPersonName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="start"
            android:hint="Tytuł" />

        <Button
            android:id="@+id/upload"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="600dp"
            android:background="@color/purple_500"
            android:gravity="center_horizontal"
            android:text="Załaduj" />

        <ImageView
            android:id="@+id/post_image_blog"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_alignParentTop="true"
            android:layout_marginTop="114dp"
            android:background="@color/purple_500"
            android:minHeight="200dp"
            android:scaleType="fitXY" />






    </LinearLayout>





</RelativeLayout>

Fragment kodu pokazujący  „Post opublikowany” lub wymóg „ Nie podano tytułu”:

upload.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            String title = title.blog.getText().toString();
           
            
            if (TextUtils.isEmpty(title)) {
                title_blog.setError("Nie podano tytułu");
            }
            else {
                uploadData(title);
            }
        }
    });
}

private void uploadData(String title) {

    pd.setMessage("Post opublikowany");
    pd.show();

    final String timeStamp = String.valueOf(System.currentTimeMillis());

    String filepath = "Posts/"+"post_"timeStamp;



   Okno widoczne po zalogowaniu z rozwijanym menu- możliwość dodania wpisu; możliwość wylogowania się




Fragment kodu pokazujący rozwijane  menu z kategoriami „Dodaj post” oraz „Wyloguj się”. Okno jest widoczne po zalogowaniu się do aplikacji:
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <item
        android:title="Wyloguj się"
        android:id="@+id/action_logout"
        app:showAsAction="never"/>

    <item
        android:title="Dodaj post"
        android:id="@+id/action_add_post"
        android:icon="@drawable/ic_baseline_add_circle_24"
        app:showAsAction="always"/>

</menu>



Wygląd bazy danych, do której przesyłane są dane nowo zarejestrowanych użytkowników:
 


Wygląd dodatkowych opcji możliwych do wykorzystania jako administrator bazy danych: usunięcie użytkownika, reset hasła, zablokowanie użytkownika, dodanie nowego użytkownika
 
