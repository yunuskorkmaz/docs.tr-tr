---
title: Infer.NET ve dayalı programlamasında bir oyun eşleştirme listesi uygulaması oluşturma
description: Basitleştirilmiş bir Trueskıll sürümüne göre bir oyun eşleme listesi uygulaması oluşturmak için dayalı Programming with Infer.NET ile nasıl kullanacağınızı öğrenin.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: aa3ad9528238e4f5a5eb187af71f2d2da1ea9cba
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855791"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Infer.NET ve dayalı programlamasında bir oyun eşleştirme listesi uygulaması oluşturma

Bu nasıl yapılır Kılavuzu, Infer.NET kullanarak dayalı programlama hakkında sizi öğretir. Dayalı programlama, özel modellerin bilgisayar programları olarak ifade edildiği bir makine öğrenimi yaklaşımıdır. Modellerdeki etki alanı bilgilerini ekleme ve makine öğrenimi sisteminin daha yoruma tablosu olmasını sağlar. Ayrıca çevrimiçi çıkarımı destekler: yeni veri geldiğinde öğrenme işlemi. Infer.NET, Azure, Xbox ve Bing 'de Microsoft 'taki çeşitli ürünlerde kullanılır.

## <a name="what-is-probabilistic-programming"></a>Dayalı programlama nedir?

Dayalı programlama, gerçek dünyada işlemlerin istatistiksel modellerini oluşturmanızı sağlar.

## <a name="prerequisites"></a>Önkoşullar

- Yerel geliştirme ortamı kurulumu

  Bu nasıl yapılır Kılavuzu, geliştirme için kullanabileceğiniz bir makineniz olmasını bekler. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, MacOS, Windows veya Linux 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. Yeni bir komut istemi açın ve aşağıdaki komutları çalıştırın:

```console
dotnet new console -o myApp
cd myApp
```

`dotnet` Komut `new` türünde bir`console`uygulama oluşturur. Parametresi `-o` , uygulamanızın depolandığı yerde adlı `myApp` bir dizin oluşturur ve gerekli dosyalarla doldurur. `cd myApp` Komut sizi yeni oluşturulan uygulama dizinine koyar.

## <a name="install-infernet-package"></a>Infer.NET paketi 'ni yükler

Infer.NET kullanmak için `Microsoft.ML.Probabilistic.Compiler` paketini yüklemeniz gerekir. Komut isteminde aşağıdaki komutu çalıştırın:

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Modelinizi tasarlama

Örnek örnek, ofiste oynatılan tablo tenis veya ipsbol eşleşmelerini kullanır. Her eşleşmenin katılımcıları ve sonuçları vardır.  Player 'ın yeteneklerini bu verilerden çıkarsmak istiyorsunuz. Her oyuncunun normal olarak dağıtılmış bir beceri yeteneklerine sahip olduğunu ve verilen eşleşme performansının bu yeteneğin gürültülü bir sürümüdür olduğunu varsayalım. Veriler, kazananın performansından daha büyük olacak şekilde kazanan performansı kısıtlar. Bu, popüler [Trueskıll](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) modelinin, takımları, çizmeler ve diğer uzantıları da destekleyen basitleştirilmiş bir sürümüdür. Bu modelin [Gelişmiş bir sürümü](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) , war 'ın en iyi satan oyun başlıklarında bir eşleme yapmak için kullanılır.

Çıkarılan oynatıcı yeteneklerini, varyanslarıyla birlikte listeleyerek yetenekler etrafında belirsizlik ölçüsünün ölçülebilinecek şekilde listeetmeniz gerekir.

*Oyun sonucu örnek verileri*

Oyun |Masının | Loser dili
---------|----------|---------
 1\. | Oyuncu 0 | Oyuncu 1
 2 | Oyuncu 0 | Oyuncu 3
 3 | Oyuncu 0 | Oyuncu 4
 4 | Oyuncu 1 | 2\. oyuncu
 5 | Oyuncu 3 | Oyuncu 1
 6 | Oyuncu 4 | 2\. oyuncu

Örnek verilere daha yakından baktığımızda, oyuncuların 3 ve 4 ' te bir kazanç ve bir kayıp olduğunu fark edeceksiniz. Ayrıca, dayalı programlamanın nasıl göründüğünü görelim. Ayrıca, Office ile eşleşen listeleri ABD geliştiricilerine göre sıfır olduğundan, bir oyuncu sıfır olduğunu fark edebilirsiniz.

## <a name="write-some-code"></a>Kod yazın

Modeli tasarladıktan sonra, Infer.NET modelleme API 'sini kullanarak bunu bir dayalı programı olarak ifade etmek zaman alabilir. En `Program.cs` sevdiğiniz metin düzenleyicisinde açın ve tüm içeriğini aşağıdaki kodla değiştirin:

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

Sonuçlarınız aşağıdakine benzer olmalıdır:

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

Sonuçlarda, Player 3 ' ün modelimize göre Player 4 ' ten biraz daha yüksek bir şekilde derecelendirdiğine dikkat edin. Bunun nedeni, Player 3 ' ün üzerindeki oyuncu 1 ' in oyuncu 2 ' den Player 4 ' ten büyük bir oyuncu 2 ' den daha önemli olduğundan, oyuncu 1 ' in oyuncu 2 ' ye göz önünde Oyuncu 0, genel temp 'dir!

## <a name="keep-learning"></a>Öğrenimi tut

İstatistiksel modellerin tasarlanmasıyla ilgili bir beceri vardır. Microsoft Research Cambridge ekibi, makaleye bir giriş sunan [ücretsiz bir çevrimiçi kitap](http://mbmlbook.com/)yazdı. Bu kitabın Bölüm 3 ' te Trueskıll modeli daha ayrıntılı bir şekilde ele alınmaktadır. Bir model aklınızda olduktan sonra, Infer.NET Web sitesindeki [kapsamlı belgeleri](https://dotnet.github.io/infer/) kullanarak kodu koda dönüştürebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Öğrenmeye devam etmek ve daha fazla örnek bulmak için Infer.NET GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/çıkarım GitHub deposu](https://github.com/dotnet/infer)
