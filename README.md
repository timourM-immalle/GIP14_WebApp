# GIP14_WebApp
## Voorbereidingen
* use-case: ![alt text](https://github.com/timourM-immalle/GIP14_WebApp/blob/master/AfbeeldingenVoorbereidingen/Idee.PNG)
* ER: ![alt text](https://github.com/timourM-immalle/GIP14_WebApp/blob/master/AfbeeldingenVoorbereidingen/ERDiagram.PNG)
* database-schema: ![alt text](https://github.com/timourM-immalle/GIP14_WebApp/blob/master/AfbeeldingenVoorbereidingen/Databaseschema.PNG)
* model-klassen-voorstel:
```C#
public class Leerkrachten
{
  public int Id { get; set; }
  public string Voornaam { get; set; }
  public string Achternaam { get; set; }
  public List<Vakken> Opleidingsonderdelen { get; set; }
  public string Email { get; set; }
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
  public Leerkrachten Docenten { get; set; }
  public Leerlingen Scholieren { get; set; }
  public double Score { get; set; }
  public double Mediaan { get; set; }
}

public class Punten
{
  public int Id { get; set; }
  public double Score { get; set; }
  public Leerlingen Scholier { get; set; }
}
```
