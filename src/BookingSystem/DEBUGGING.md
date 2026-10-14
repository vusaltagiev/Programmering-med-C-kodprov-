#1 Vilket fel undersökte du? 
Jag undersökte ett fel som uppstod när jag försökte boka en tid i bokningssystemet. Systemet kraschade om användaren skrev in text i stället för siffror när programmet efterfrågade ett deltagare (Participants)

#2 Hur återskapade du felet?
Jag startade programmet, navigerade till menyn för att skapa en ny bokning, och skrev in en textsträng (six) när systemet efterfrågade hur många deltagare som skulle delta.

#3 Vilket resultat fick du?
Programmet kraschade omedelbart och kastade ett undantag, vilket gjorde att konsolapplikationen stängdes av abrupt.

#4 Vilket resultat skulle du ha fått?
Programmet borde ha hanterat den ogiltiga inmatningen på ett sätt där det kontroleras, visat ett tydligt felmeddelande för användaren om användaren skriver textsträng och låtit användaren försöka igen utan att systemet krascha.

#5 Vilken del av koden orsakade felet?
Felet fanns i konsolhanteringen i BookingConsole.cs där inmatningen från Console.ReadLine() lästes in och direkt konverterades med int.Parse().

#6 Varför gav koden ett felaktigt resultat?
Metoden int.Parse() förväntar sig en textsträng som enbart innehåller numeriska tecken som kan tolkas som ett heltal. När den fick ren text (bokstäver) kunde den inte utföra omvandlingen och kraschade eftersom koden saknade felhantering för ogiltiga datatyper.

#7 Vad ändrade du?
Jag ändrade inläsningslogiken så att den istället använder int.TryParse(), vilket gör att programmet kan kontrollera med true och fals om inmatningen är ett giltigt heltal innan den används, och annars skriva ut ett felmeddelande.

#8 Hur kontrollerade du att ändringen fungerade?
Jag körde programmet igen och skrev in bokstäver istället för siffror i deltagarfältet och såg att programmet nu svarade med ett snyggt felmeddelande i stället för att krascha. Om man matade in text fick man medelande "Enter a valid number". 

#9 Vilket automatiserat test skyddar mot att felet återkommer?
Eftersom det här felet hände direkt i konsolen när man skrev in text, finns det inget automatiskt test för det. Jag har i stället testat det manuellt genom att köra programmet och skriva in bokstäver för att se att det inte kraschar.