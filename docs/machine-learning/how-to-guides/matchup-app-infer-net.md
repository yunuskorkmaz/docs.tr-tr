---
title: Infer.NET ve olasılığa dayalı programlama ile bir oyun eşleme listesi uygulaması oluşturma
description: Olasılığa dayalı programlama ile Infer.NET TrueSkill basitleştirilmiş bir sürümünü temel alan bir oyun matchup listesi uygulaması oluşturmak için nasıl kullanılacağını keşfedin.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 85cb3753ae19e7ca64002eb7c26b44b6f7d41e4f
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211429"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Infer.NET ve olasılığa dayalı programlama ile bir oyun eşleme listesi uygulaması oluşturma

Bu nasıl yapılır kılavuzunda Infer.NET kullanarak olasılığa dayalı programlama hakkında size öğretir. Olasılığa dayalı programlama bir machine learning burada özel modelleri bilgisayar programları olarak ifade edilir yaklaşımdır. Bu etki alanı bilgisini modellerindeki birleştirmek için izin verir ve makine öğrenimi sistemi daha yorumlanabilirinde yapar. Ayrıca, çevrimiçi çıkarımı – yeni veriler ulaştıkça öğrenme işlemi destekler. Microsoft Azure, Xbox ve Bing çeşitli ürünlerin Infer.NET kullanılır.

## <a name="what-is-probabilistic-programming"></a>Olasılığa dayalı programlama nedir?

Olasılığa dayalı programlama gerçek işlemlerin istatistiksel modelleri oluşturmanıza olanak sağlar.

## <a name="prerequisites"></a>Önkoşullar

- Yerel geliştirme ortamı Kurulumu

  Bu nasıl yapılır kılavuzunda geliştirme için kullanabileceğiniz bir makine olmasını bekliyor. .NET [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) öğretici Mac, PC ve Linux üzerinde yerel geliştirme ortamınızı ayarlama yönergeleri sahiptir.

## <a name="create-your-app"></a>Uygulamanızı oluşturma

1. Yeni bir komut istemi açın ve aşağıdaki komutları çalıştırın:

```console
dotnet new console -o myApp
cd myApp
```

`dotnet` Komut oluşturur bir `new` uygulama türünün `console`. `-o` Parametresi adlı bir dizin oluşturur `myApp` dosyaları uygulamanızı nerede depolanır ve gerekli ile doldurur. `cd myApp` Komutu, yeni oluşturulan uygulama dizine koyar.

## <a name="install-infernet-package"></a>Infer.NET paketini yükle

Yüklemeniz gerekiyor Infer.NET kullanılacak `Microsoft.ML.Probabilistic.Compiler` paket. Komut isteminde aşağıdaki komutu çalıştırın:

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Model tasarlama

Foosball eşleşen office içinde yürütülen ya da örnek örnek tablo tenis kullanır. Katılımcılar ve her bir eşleştirmeyi sonucu var.  Bu verilerden oyuncunun becerileri Infer istiyorsunuz. Normal olarak dağıtılmış bir görünmeyen becerisi her oyuncusu içeriyor ve belirli eşleşme performanslarını bu beceri gürültülü sürümüdür varsayılır. Veri ödül performans kaybeden'ın performansı daha büyük olacak şekilde kısıtlar. Basitleştirilmiş bir sürümünü popüler budur [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, hangi takımları çizer ve diğer uzantılar da destekler. Bir [Gelişmiş sürüm](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) bu modeli, en çok satan oyun başlıklarında Halo ve Gears, War matchmaking için kullanılır.

Çıkarsanan player becerileri yanı sıra kendi fark – becerileri belirsizliğin ölçü liste gerekir.

*Oyun sonucu örnek veriler*

Oyun |Kazanan | Kaybeden
---------|----------|---------
 1. | Oynatıcı 0 | Oynatıcı 1
 2 | Oynatıcı 0 | Player 3
 3 | Oynatıcı 0 | Player 4
 4 | Oynatıcı 1 | Oynatıcı 2
 5 | Player 3 | Oynatıcı 1
 6 | Player 4 | Oynatıcı 2

Yakından ile örnek veriler, 3 ve 4 oyuncu bir win ve bir kaybı olduğunu fark edeceksiniz. Olasılığa dayalı programlama kullanma gibi hangi sıralamasına Ara görelim. Ayrıca bir oynatıcı sıfır bile office eşleşme liste sıfır bize geliştiriciler tabanlı olduğundan dikkat edin.

## <a name="write-some-code"></a>Bazı kodlar yazma

Model tasarlanan bu API modelleme Infer.NET kullanarak olasılığa dayanan bir program olarak express zamanı geldi. Açık `Program.cs` sık kullandığınız metin düzenleyicinizde ve tüm içeriğini aşağıdaki kodla değiştirin:

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

Komut isteminde aşağıdaki komutu çalıştırın:

```console
dotnet run
```

## <a name="results"></a>Sonuçlar

Sonuçlar aşağıdakine benzer olmalıdır:

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

Sonuçlarda oyuncu 3 4 oyuncu modelimizi göre biraz daha sıralayan dikkat edin. Oynatıcı 3 player 1 üzerinde tek tek oynatıcı 4 oyuncu 2 – üzerinden daha önemli çünkü 1 oyuncu vuruş player 2 unutmayın. Oynatıcı 0 Genel uzmanının sunuluyor

## <a name="keep-learning"></a>Öğrenme tutun

İstatistiksel modelleri tasarlama, kendi kendine bir yetenektir. Microsoft Research Cambridge takım yazılmış bir [ücretsiz çevrimiçi kitap](http://mbmlbook.com/), makalede size bir giriş sağlar. Bölüm 3 kitabın TrueSkill modeli daha ayrıntılı bir şekilde anlatılmaktadır. Göz önünde bir modeli oluşturduktan sonra bu kodu kullanarak dönüştürebilirsiniz [dokümantasyonuna](https://dotnet.github.io/infer/) Infer.NET Web sitesinde.

## <a name="next-steps"></a>Sonraki adımlar

Almaya devam etmek ve diğer örnekleri bulmak için Infer.NET GitHub havuzuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/Infer GitHub deposu](https://github.com/dotnet/infer)
