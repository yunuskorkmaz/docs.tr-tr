---
title: Infer.NET ve dayalı programlamasında bir oyun eşleştirme listesi uygulaması oluşturma
description: Basitleştirilmiş bir Trueskıll sürümüne göre bir oyun eşleme listesi uygulaması oluşturmak için dayalı Programming with Infer.NET ile nasıl kullanacağınızı öğrenin.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 69515c7b3518c35bf84335c453408b1466f93f34
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774540"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="f115b-103">Infer.NET ve dayalı programlamasında bir oyun eşleştirme listesi uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f115b-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="f115b-104">Bu nasıl yapılır Kılavuzu, Infer.NET kullanarak dayalı programlama hakkında sizi öğretir.</span><span class="sxs-lookup"><span data-stu-id="f115b-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="f115b-105">Dayalı programlama, özel modellerin bilgisayar programları olarak ifade edildiği bir makine öğrenimi yaklaşımıdır.</span><span class="sxs-lookup"><span data-stu-id="f115b-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="f115b-106">Modellerdeki etki alanı bilgilerini ekleme ve makine öğrenimi sisteminin daha yoruma tablosu olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f115b-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="f115b-107">Ayrıca çevrimiçi çıkarımı destekler: yeni veri geldiğinde öğrenme işlemi.</span><span class="sxs-lookup"><span data-stu-id="f115b-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="f115b-108">Infer.NET, Azure, Xbox ve Bing 'de Microsoft 'taki çeşitli ürünlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f115b-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="f115b-109">Dayalı programlama nedir?</span><span class="sxs-lookup"><span data-stu-id="f115b-109">What is probabilistic programming?</span></span>

<span data-ttu-id="f115b-110">Dayalı programlama, gerçek dünyada işlemlerin istatistiksel modellerini oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f115b-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f115b-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f115b-111">Prerequisites</span></span>

- <span data-ttu-id="f115b-112">Yerel geliştirme ortamı kurulumu</span><span class="sxs-lookup"><span data-stu-id="f115b-112">Local development environment setup</span></span>

  <span data-ttu-id="f115b-113">Bu nasıl yapılır Kılavuzu, geliştirme için kullanabileceğiniz bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="f115b-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="f115b-114">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, MacOS, Windows veya Linux 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="f115b-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="f115b-115">Uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="f115b-115">Create your app</span></span>

1. <span data-ttu-id="f115b-116">Yeni bir komut istemi açın ve aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f115b-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="f115b-117">@No__t_0 komutu `console` türünde bir `new` uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f115b-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="f115b-118">@No__t_0 parametresi, uygulamanızın depolandığı `myApp` adlı bir dizin oluşturur ve gerekli dosyalarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="f115b-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="f115b-119">@No__t_0 komutu sizi yeni oluşturulan uygulama dizinine koyar.</span><span class="sxs-lookup"><span data-stu-id="f115b-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="f115b-120">Infer.NET paketi 'ni yükler</span><span class="sxs-lookup"><span data-stu-id="f115b-120">Install Infer.NET package</span></span>

<span data-ttu-id="f115b-121">Infer.NET kullanmak için `Microsoft.ML.Probabilistic.Compiler` paketini yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f115b-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="f115b-122">Komut isteminde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f115b-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="f115b-123">Modelinizi tasarlama</span><span class="sxs-lookup"><span data-stu-id="f115b-123">Design your model</span></span>

<span data-ttu-id="f115b-124">Örnek örnek, ofiste oynatılan tablo tenis veya ipsbol eşleşmelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f115b-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="f115b-125">Her eşleşmenin katılımcıları ve sonuçları vardır.</span><span class="sxs-lookup"><span data-stu-id="f115b-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="f115b-126">Player 'ın yeteneklerini bu verilerden çıkarsmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f115b-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="f115b-127">Her oyuncunun normal olarak dağıtılmış bir beceri yeteneklerine sahip olduğunu ve verilen eşleşme performansının bu yeteneğin gürültülü bir sürümüdür olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="f115b-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="f115b-128">Veriler, kazananın performansından daha büyük olacak şekilde kazanan performansı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f115b-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="f115b-129">Bu, popüler [Trueskıll](https://www.microsoft.com/research/project/trueskill-ranking-system/) modelinin, takımları, çizmeler ve diğer uzantıları da destekleyen basitleştirilmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f115b-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="f115b-130">Bu modelin [Gelişmiş bir sürümü](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) , war 'ın en iyi satan oyun başlıklarında bir eşleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f115b-130">An [advanced version](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="f115b-131">Çıkarılan oynatıcı yeteneklerini, varyanslarıyla birlikte listeleyerek yetenekler etrafında belirsizlik ölçüsünün ölçülebilinecek şekilde listeetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f115b-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="f115b-132">*Oyun sonucu örnek verileri*</span><span class="sxs-lookup"><span data-stu-id="f115b-132">*Game result sample data*</span></span>

<span data-ttu-id="f115b-133">Oyun</span><span class="sxs-lookup"><span data-stu-id="f115b-133">Game</span></span> |<span data-ttu-id="f115b-134">Masının</span><span class="sxs-lookup"><span data-stu-id="f115b-134">Winner</span></span> | <span data-ttu-id="f115b-135">Loser dili</span><span class="sxs-lookup"><span data-stu-id="f115b-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="f115b-136">1\.</span><span class="sxs-lookup"><span data-stu-id="f115b-136">1</span></span> | <span data-ttu-id="f115b-137">Oyuncu 0</span><span class="sxs-lookup"><span data-stu-id="f115b-137">Player 0</span></span> | <span data-ttu-id="f115b-138">Oyuncu 1</span><span class="sxs-lookup"><span data-stu-id="f115b-138">Player 1</span></span>
 <span data-ttu-id="f115b-139">2</span><span class="sxs-lookup"><span data-stu-id="f115b-139">2</span></span> | <span data-ttu-id="f115b-140">Oyuncu 0</span><span class="sxs-lookup"><span data-stu-id="f115b-140">Player 0</span></span> | <span data-ttu-id="f115b-141">Oyuncu 3</span><span class="sxs-lookup"><span data-stu-id="f115b-141">Player 3</span></span>
 <span data-ttu-id="f115b-142">3</span><span class="sxs-lookup"><span data-stu-id="f115b-142">3</span></span> | <span data-ttu-id="f115b-143">Oyuncu 0</span><span class="sxs-lookup"><span data-stu-id="f115b-143">Player 0</span></span> | <span data-ttu-id="f115b-144">Oyuncu 4</span><span class="sxs-lookup"><span data-stu-id="f115b-144">Player 4</span></span>
 <span data-ttu-id="f115b-145">4</span><span class="sxs-lookup"><span data-stu-id="f115b-145">4</span></span> | <span data-ttu-id="f115b-146">Oyuncu 1</span><span class="sxs-lookup"><span data-stu-id="f115b-146">Player 1</span></span> | <span data-ttu-id="f115b-147">2\. oyuncu</span><span class="sxs-lookup"><span data-stu-id="f115b-147">Player 2</span></span>
 <span data-ttu-id="f115b-148">5</span><span class="sxs-lookup"><span data-stu-id="f115b-148">5</span></span> | <span data-ttu-id="f115b-149">Oyuncu 3</span><span class="sxs-lookup"><span data-stu-id="f115b-149">Player 3</span></span> | <span data-ttu-id="f115b-150">Oyuncu 1</span><span class="sxs-lookup"><span data-stu-id="f115b-150">Player 1</span></span>
 <span data-ttu-id="f115b-151">6</span><span class="sxs-lookup"><span data-stu-id="f115b-151">6</span></span> | <span data-ttu-id="f115b-152">Oyuncu 4</span><span class="sxs-lookup"><span data-stu-id="f115b-152">Player 4</span></span> | <span data-ttu-id="f115b-153">2\. oyuncu</span><span class="sxs-lookup"><span data-stu-id="f115b-153">Player 2</span></span>

<span data-ttu-id="f115b-154">Örnek verilere daha yakından baktığımızda, oyuncuların 3 ve 4 ' te bir kazanç ve bir kayıp olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f115b-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="f115b-155">Ayrıca, dayalı programlamanın nasıl göründüğünü görelim.</span><span class="sxs-lookup"><span data-stu-id="f115b-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="f115b-156">Ayrıca, Office ile eşleşen listeleri ABD geliştiricilerine göre sıfır olduğundan, bir oyuncu sıfır olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f115b-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="f115b-157">Kod yazın</span><span class="sxs-lookup"><span data-stu-id="f115b-157">Write some code</span></span>

<span data-ttu-id="f115b-158">Modeli tasarladıktan sonra, Infer.NET modelleme API 'sini kullanarak bunu bir dayalı programı olarak ifade etmek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="f115b-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="f115b-159">En sevdiğiniz metin düzenleyicisinde `Program.cs` açın ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f115b-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="f115b-160">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f115b-160">Run your app</span></span>

<span data-ttu-id="f115b-161">Komut isteminde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f115b-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="f115b-162">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="f115b-162">Results</span></span>

<span data-ttu-id="f115b-163">Sonuçlarınız aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f115b-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="f115b-164">Sonuçlarda, Player 3 ' ün modelimize göre Player 4 ' ten biraz daha yüksek bir şekilde derecelendirdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f115b-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="f115b-165">Bunun nedeni, Player 3 ' ün üzerindeki oyuncu 1 ' in oyuncu 2 ' den Player 4 ' ten büyük bir oyuncu 2 ' den daha önemli olduğundan, oyuncu 1 ' in oyuncu 2 ' ye göz önünde</span><span class="sxs-lookup"><span data-stu-id="f115b-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="f115b-166">Oyuncu 0, genel temp 'dir!</span><span class="sxs-lookup"><span data-stu-id="f115b-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="f115b-167">Öğrenimi tut</span><span class="sxs-lookup"><span data-stu-id="f115b-167">Keep learning</span></span>

<span data-ttu-id="f115b-168">İstatistiksel modellerin tasarlanmasıyla ilgili bir beceri vardır.</span><span class="sxs-lookup"><span data-stu-id="f115b-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="f115b-169">Microsoft Research Cambridge ekibi, makaleye bir giriş sunan [ücretsiz bir çevrimiçi kitap](http://mbmlbook.com/)yazdı.</span><span class="sxs-lookup"><span data-stu-id="f115b-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="f115b-170">Bu kitabın Bölüm 3 ' te Trueskıll modeli daha ayrıntılı bir şekilde ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f115b-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="f115b-171">Bir model aklınızda olduktan sonra, Infer.NET Web sitesindeki [kapsamlı belgeleri](https://dotnet.github.io/infer/) kullanarak kodu koda dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f115b-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f115b-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f115b-172">Next steps</span></span>

<span data-ttu-id="f115b-173">Öğrenmeye devam etmek ve daha fazla örnek bulmak için Infer.NET GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="f115b-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f115b-174">DotNet/çıkarım GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="f115b-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
