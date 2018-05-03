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

## Uitvoering
De webapplicatie is niet klaargeraakt. In het begin kende ik de structuur van een MVC-framework niet goed genoeg, waardoor ik begonnen ben met alle code in een `.cshtml`-file te zetten:
```C#
@page

@{
    //ViewData["Title"] = "NieuwPuntentabel";
    Layout = null;

    Dictionary<string, int> aantalLeerlingen = new Dictionary<string, int>()
    {
        {"6ITN", 10},
        {"6OIT", 18},
        {"6OM", 12},
        {"6OMT", 10},
        {"6CM", 10},
    };
}
<!--model voor communicatie met database-->
<div>Welke Klas?</div>
<select id="geselecteerdeKlas">
    @foreach (KeyValuePair<string, int> kvp in aantalLeerlingen)
    {
        <option value="@kvp.Key">@kvp.Key</option>
    }
</select>

<div>onderwerp:</div><textarea></textarea>
<div>max. aantal punten:</div><textarea id="maxPunten"></textarea>

<table>
    <tr>
        <th>leerling</th>
        <th>score</th>
        <th>maximum</th>
    </tr>
    @foreach (KeyValuePair<string, int> kvp in aantalLeerlingen)//Juist? Nee, lln moeten uit database gehaald worden
    {
        <tr>
            <td></td>
            <td><input type="text" /></td>
            <td><script>document.write(document.getElementById("maxPunten").value);</script></td><!--Hoe kan ik hier de inhoud van maxPunten opvragen?-->
        </tr>
    }


</table>

<button id="btnOpslaan">Opslaan</button>
```
Dit lijkt misschien oké, maar zo werk ik eigenlijk het Framework tegen (zeker aangezien ik amper rekening hield met models en controllers).

Verder heb ik er ook nog Google Authentication in geprogrammeerd (in `Startup.cs`):
```C#
public void ConfigureServices(IServiceCollection services)
{
  services.AddMvc();
  
  services.AddDbContext<MyFirstWebAppIIContext>(options =>
                    options.UseSqlServer(Configuration.GetConnectionString("MyFirstWebAppIIContext")));
  
  services.AddAuthentication().AddGoogle(googleOptions =>
  {
    googleOptions.ClientId = "478889081647-3p6rdl5m0f3m2paih3i98p6oimd8ncn5.apps.googleusercontent.com";
    googleOptions.ClientSecret = "WR4atVdeFbaXD3-Si9WCwJZE";
  }
}
```
Sindsdien gebruik ik poort `44320`.

Ten slotte bestaat er ook nog een simpele pagina `http://localhost:44320/Punts`, waarbij  men nieuwe punten kan ingeven, bewerken en wissen (het wordt opgeslagen op een database), maar veel spectaculairder is het niet geworden.
