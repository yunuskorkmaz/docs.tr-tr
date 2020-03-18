---
title: Infer.NET oyunu match-up uygulaması - olasılıkprogramlama
description: TrueSkill'in basitleştirilmiş bir sürümüne dayalı bir oyun eşleştirme listesi uygulaması oluşturmak için olasılıksal programlamayı Infer.NET ile nasıl kullanacağını keşfedin.
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 8e489d61c5e6cca53ba12b13fddd0b73c7f85ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092609"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Infer.NET ve olasılıksal programlama ile bir oyun eşleştirme listesi uygulaması oluşturun

Bu nasıl-nasıl kılavuzu Infer.NET kullanarak olasılıksal programlama hakkında öğretir. Olasılıksal programlama, özel modellerin bilgisayar programları olarak ifade edildiği bir makine öğrenimi yaklaşımıdır. Bu modellerde etki alanı bilgisi dahil edilmesine olanak sağlar ve makine öğrenme sistemi daha yorumlanabilir hale getirir. Ayrıca çevrimiçi çıkarımları destekler – yeni veriler geldikçe öğrenme süreci. Infer.NET, Microsoft'ta Azure, Xbox ve Bing'deki çeşitli ürünlerde kullanılır.

## <a name="what-is-probabilistic-programming"></a>Olasılıksal programlama nedir?

Olasılıksal programlama, gerçek dünya süreçlerinin istatistiksel modellerini oluşturmanıza olanak tanır.

## <a name="prerequisites"></a>Önkoşullar

- Yerel geliştirme ortamı kurulumu

  Bu nasıl yapılabilir kılavuzu geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) macOS, Windows veya Linux'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. Yeni bir komut istemi açın ve aşağıdaki komutları çalıştırın:

```dotnetcli
dotnet new console -o myApp
cd myApp
```

Komut `dotnet` türünde `console` `new` bir uygulama oluşturur. Parametre, `-o` uygulamanızın depolandığı `myApp` yer adlı bir dizin oluşturur ve uygulamayı gerekli dosyalarla doldurur. Komut `cd myApp` sizi yeni oluşturulan uygulama dizinine sokar.

## <a name="install-infernet-package"></a>Infer.NET paketi yükleyin

Infer.NET kullanmak için `Microsoft.ML.Probabilistic.Compiler` paketi yüklemeniz gerekir. Komut isteminizde aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Modelinizi tasarla

Örnek örnek, ofiste oynanan masa tenisi veya langırt maçlarını kullanır. Her maçın katılımcıları ve sonucu sizde.  Bu verilerden oyuncunun becerilerini çıkarmak istiyorum. Her oyuncunun normalde dağıtılmış gizli bir beceriye sahip olduğunu ve verilen maç performansının bu becerinin gürültülü bir versiyonu olduğunu varsayalım. Veriler, kazananın performansını kaybedenin performansından daha fazla olmak üzere kısıtlar. Bu, takımları, berabere beraberliği ve diğer uzantıları da destekleyen popüler [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) modelinin basitleştirilmiş bir sürümüdür. Bu modelin [gelişmiş bir sürümü](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) en çok satan oyun başlıkları Halo ve Gears of War çöpçatanlık için kullanılır.

Onların varyans ile birlikte, çıkarılan oyuncu becerilerini listelemek gerekir - becerileri etrafında belirsizlik ölçüsü.

*Oyun sonucu örnek verileri*

Oyun |Kazanan | Kaybeden
---------|----------|---------
 1 | Oyuncu 0 | Oyuncu 1
 2 | Oyuncu 0 | Oyuncu 3
 3 | Oyuncu 0 | Oyuncu 4
 4 | Oyuncu 1 | Oyuncu 2
 5 | Oyuncu 3 | Oyuncu 1
 6 | Oyuncu 4 | Oyuncu 2

Örnek verilere daha yakından baktığınızda, 3 ve 4 numaralı oyuncuların hem bir galibiyet hem de bir mağlubiyet olduğunu fark edeceksiniz. Sıralamaların olasılıksal programlamayı kullanarak nasıl göründüğünü görelim. Dikkat edin ayrıca bir oyuncu sıfır çünkü hatta ofis maç listeleri sıfır biz geliştiriciler için dayanır.

## <a name="write-some-code"></a>Bazı kod yazma

Modeli tasarladıktan sonra, Infer.NET modelleme API kullanarak olasılıksal bir program olarak ifade etmek zamanı. En `Program.cs` sevdiğiniz metin düzenleyicisinde açın ve tüm içeriğini aşağıdaki kodla değiştirin:

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

Komut isteminizde aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet run
```

## <a name="results"></a>Sonuçlar

Sonuçlarınız aşağıdakilere benzer olmalıdır:

```console
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

Sonuçlarda, oyuncu 3 bizim modele göre oyuncu 4 biraz daha yüksek sırada olduğunu unutmayın. Çünkü oyuncu 3'ün oyuncu 1'e karşı kazandığı zafer, oyuncu 4'ün oyuncu 2'ye karşı kazandığı zaferden daha önemlidir – 1 oyuncunun 2'yi yendiğini unutmayın. Oyuncu 0 genel şampiyon!

## <a name="keep-learning"></a>Öğrenmeye devam edin

İstatistiksel modeller tasarlamak kendi başına bir beceridir. Microsoft Research Cambridge ekibi [ücretsiz](http://mbmlbook.com/)bir online kitap yazmıştır , hangi makaleye nazik bir giriş verir. Bu kitabın Bölüm 3 daha ayrıntılı olarak TrueSkill modeli kapsar. Bir kez aklınızda bir model var, Infer.NET web sitesinde [kapsamlı belgeleri](https://dotnet.github.io/infer/) kullanarak kod dönüştürebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Öğrenmeye devam etmek ve daha fazla örnek bulmak için Infer.NET GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [dotnet/infer GitHub deposu](https://github.com/dotnet/infer)
