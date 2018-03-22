# GIP14_WebApp
## Voorbereidingen
* use-case: ![alt text](https://github.com/timourM-immalle/GIP14_WebApp/blob/master/UseCase.PNG)
* ER: ![alt text](https://github.com/timourM-immalle/GIP14_WebApp/blob/master/ER.PNG)
* database-schema: ![alt text](https://github.com/timourM-immalle/GIP14_WebApp/blob/master/Databaseschema.PNG)
* model-klassen-voorstel:
```C#
public class Leerkrachten
{
  public int Id { get; set; }
  public string Voornaam { get; set; }
  public string Achternaam { get; set; }
  public string Email { get; set; }
  public List<Vakken> Opleidingsonderdelen { get; set; }
}

public class Leerlingen
{
  public int Klasnummer { get; set; }
  public string Voornaam { get; set; }
  public string Achternaam { get; set; }
  public string Klas { get; set; }
  public List<Vakken> Opleidingsonderdelen { get; set; }
  public double Score { get; set; }
}

public class Vakken
{
  public int Id { get; set; }
  public string Naam { get; set; }
  public List<string> Klassen { get; set; }
  public Leerkrachten Leerkracht { get; set; }
  public double Score { get; set; }
  public double Mediaan { get; set; }
}

public class Punten
{
  public int Id { get; set; }
  public Vakken Vak { get; set; }
  public double Score { get; set; }
  public Leerlingen Leerling { get; set; }
}
```
