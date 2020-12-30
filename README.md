# MauryDev.KoGaMaLeaderboardAPI

## Methods

- `GetLeaderboard(int count): Task<Dictionary<int,ScoreInfo>>`

- `GetLeaderboardFromUser(int id ,int count): Task<Dictionary<int,ScoreInfo>>`

## ScoreInfo

- xp
- position
- avatar
- id
- name

## Example

Main.cs
```cs
using System.Globalization;
using MauryDev.KoGaMaLeaderboardAPI;
using System;

class Program
{
  static void Main(string[] args)
  {
    var scores = Leaderboard.GetLeaderboard(100).Result;
    foreach (var score in scores.Values)
    {
      Console.WriteLine("Position: " + FormatNumber(score.position));
      Console.WriteLine("Username: " + score.name);
      Console.WriteLine("XP: " + FormatNumber(score.xp));
      Console.ReadLine();
    }
    Console.ReadLine();
  }
  static string FormatNumber(int value)
  {
    return value.ToString("n", new NumberFormatInfo() { NumberGroupSeparator = " ", NumberDecimalDigits = 0 });
  }
}
```
