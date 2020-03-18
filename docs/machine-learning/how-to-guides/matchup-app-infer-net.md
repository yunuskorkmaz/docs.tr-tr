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
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="3c469-103">Infer.NET ve olasılıksal programlama ile bir oyun eşleştirme listesi uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="3c469-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="3c469-104">Bu nasıl-nasıl kılavuzu Infer.NET kullanarak olasılıksal programlama hakkında öğretir.</span><span class="sxs-lookup"><span data-stu-id="3c469-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="3c469-105">Olasılıksal programlama, özel modellerin bilgisayar programları olarak ifade edildiği bir makine öğrenimi yaklaşımıdır.</span><span class="sxs-lookup"><span data-stu-id="3c469-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="3c469-106">Bu modellerde etki alanı bilgisi dahil edilmesine olanak sağlar ve makine öğrenme sistemi daha yorumlanabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3c469-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="3c469-107">Ayrıca çevrimiçi çıkarımları destekler – yeni veriler geldikçe öğrenme süreci.</span><span class="sxs-lookup"><span data-stu-id="3c469-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="3c469-108">Infer.NET, Microsoft'ta Azure, Xbox ve Bing'deki çeşitli ürünlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c469-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="3c469-109">Olasılıksal programlama nedir?</span><span class="sxs-lookup"><span data-stu-id="3c469-109">What is probabilistic programming?</span></span>

<span data-ttu-id="3c469-110">Olasılıksal programlama, gerçek dünya süreçlerinin istatistiksel modellerini oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3c469-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3c469-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3c469-111">Prerequisites</span></span>

- <span data-ttu-id="3c469-112">Yerel geliştirme ortamı kurulumu</span><span class="sxs-lookup"><span data-stu-id="3c469-112">Local development environment setup</span></span>

  <span data-ttu-id="3c469-113">Bu nasıl yapılabilir kılavuzu geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3c469-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="3c469-114">.NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) macOS, Windows veya Linux'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3c469-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="3c469-115">Uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="3c469-115">Create your app</span></span>

1. <span data-ttu-id="3c469-116">Yeni bir komut istemi açın ve aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3c469-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="3c469-117">Komut `dotnet` türünde `console` `new` bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c469-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="3c469-118">Parametre, `-o` uygulamanızın depolandığı `myApp` yer adlı bir dizin oluşturur ve uygulamayı gerekli dosyalarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="3c469-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="3c469-119">Komut `cd myApp` sizi yeni oluşturulan uygulama dizinine sokar.</span><span class="sxs-lookup"><span data-stu-id="3c469-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="3c469-120">Infer.NET paketi yükleyin</span><span class="sxs-lookup"><span data-stu-id="3c469-120">Install Infer.NET package</span></span>

<span data-ttu-id="3c469-121">Infer.NET kullanmak için `Microsoft.ML.Probabilistic.Compiler` paketi yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c469-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="3c469-122">Komut isteminizde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3c469-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="3c469-123">Modelinizi tasarla</span><span class="sxs-lookup"><span data-stu-id="3c469-123">Design your model</span></span>

<span data-ttu-id="3c469-124">Örnek örnek, ofiste oynanan masa tenisi veya langırt maçlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c469-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="3c469-125">Her maçın katılımcıları ve sonucu sizde.</span><span class="sxs-lookup"><span data-stu-id="3c469-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="3c469-126">Bu verilerden oyuncunun becerilerini çıkarmak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="3c469-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="3c469-127">Her oyuncunun normalde dağıtılmış gizli bir beceriye sahip olduğunu ve verilen maç performansının bu becerinin gürültülü bir versiyonu olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3c469-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="3c469-128">Veriler, kazananın performansını kaybedenin performansından daha fazla olmak üzere kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="3c469-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="3c469-129">Bu, takımları, berabere beraberliği ve diğer uzantıları da destekleyen popüler [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) modelinin basitleştirilmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="3c469-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="3c469-130">Bu modelin [gelişmiş bir sürümü](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) en çok satan oyun başlıkları Halo ve Gears of War çöpçatanlık için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c469-130">An [advanced version](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="3c469-131">Onların varyans ile birlikte, çıkarılan oyuncu becerilerini listelemek gerekir - becerileri etrafında belirsizlik ölçüsü.</span><span class="sxs-lookup"><span data-stu-id="3c469-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="3c469-132">*Oyun sonucu örnek verileri*</span><span class="sxs-lookup"><span data-stu-id="3c469-132">*Game result sample data*</span></span>

<span data-ttu-id="3c469-133">Oyun</span><span class="sxs-lookup"><span data-stu-id="3c469-133">Game</span></span> |<span data-ttu-id="3c469-134">Kazanan</span><span class="sxs-lookup"><span data-stu-id="3c469-134">Winner</span></span> | <span data-ttu-id="3c469-135">Kaybeden</span><span class="sxs-lookup"><span data-stu-id="3c469-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="3c469-136">1</span><span class="sxs-lookup"><span data-stu-id="3c469-136">1</span></span> | <span data-ttu-id="3c469-137">Oyuncu 0</span><span class="sxs-lookup"><span data-stu-id="3c469-137">Player 0</span></span> | <span data-ttu-id="3c469-138">Oyuncu 1</span><span class="sxs-lookup"><span data-stu-id="3c469-138">Player 1</span></span>
 <span data-ttu-id="3c469-139">2</span><span class="sxs-lookup"><span data-stu-id="3c469-139">2</span></span> | <span data-ttu-id="3c469-140">Oyuncu 0</span><span class="sxs-lookup"><span data-stu-id="3c469-140">Player 0</span></span> | <span data-ttu-id="3c469-141">Oyuncu 3</span><span class="sxs-lookup"><span data-stu-id="3c469-141">Player 3</span></span>
 <span data-ttu-id="3c469-142">3</span><span class="sxs-lookup"><span data-stu-id="3c469-142">3</span></span> | <span data-ttu-id="3c469-143">Oyuncu 0</span><span class="sxs-lookup"><span data-stu-id="3c469-143">Player 0</span></span> | <span data-ttu-id="3c469-144">Oyuncu 4</span><span class="sxs-lookup"><span data-stu-id="3c469-144">Player 4</span></span>
 <span data-ttu-id="3c469-145">4</span><span class="sxs-lookup"><span data-stu-id="3c469-145">4</span></span> | <span data-ttu-id="3c469-146">Oyuncu 1</span><span class="sxs-lookup"><span data-stu-id="3c469-146">Player 1</span></span> | <span data-ttu-id="3c469-147">Oyuncu 2</span><span class="sxs-lookup"><span data-stu-id="3c469-147">Player 2</span></span>
 <span data-ttu-id="3c469-148">5</span><span class="sxs-lookup"><span data-stu-id="3c469-148">5</span></span> | <span data-ttu-id="3c469-149">Oyuncu 3</span><span class="sxs-lookup"><span data-stu-id="3c469-149">Player 3</span></span> | <span data-ttu-id="3c469-150">Oyuncu 1</span><span class="sxs-lookup"><span data-stu-id="3c469-150">Player 1</span></span>
 <span data-ttu-id="3c469-151">6</span><span class="sxs-lookup"><span data-stu-id="3c469-151">6</span></span> | <span data-ttu-id="3c469-152">Oyuncu 4</span><span class="sxs-lookup"><span data-stu-id="3c469-152">Player 4</span></span> | <span data-ttu-id="3c469-153">Oyuncu 2</span><span class="sxs-lookup"><span data-stu-id="3c469-153">Player 2</span></span>

<span data-ttu-id="3c469-154">Örnek verilere daha yakından baktığınızda, 3 ve 4 numaralı oyuncuların hem bir galibiyet hem de bir mağlubiyet olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3c469-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="3c469-155">Sıralamaların olasılıksal programlamayı kullanarak nasıl göründüğünü görelim.</span><span class="sxs-lookup"><span data-stu-id="3c469-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="3c469-156">Dikkat edin ayrıca bir oyuncu sıfır çünkü hatta ofis maç listeleri sıfır biz geliştiriciler için dayanır.</span><span class="sxs-lookup"><span data-stu-id="3c469-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="3c469-157">Bazı kod yazma</span><span class="sxs-lookup"><span data-stu-id="3c469-157">Write some code</span></span>

<span data-ttu-id="3c469-158">Modeli tasarladıktan sonra, Infer.NET modelleme API kullanarak olasılıksal bir program olarak ifade etmek zamanı.</span><span class="sxs-lookup"><span data-stu-id="3c469-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="3c469-159">En `Program.cs` sevdiğiniz metin düzenleyicisinde açın ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3c469-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="3c469-160">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3c469-160">Run your app</span></span>

<span data-ttu-id="3c469-161">Komut isteminizde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3c469-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="3c469-162">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="3c469-162">Results</span></span>

<span data-ttu-id="3c469-163">Sonuçlarınız aşağıdakilere benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3c469-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="3c469-164">Sonuçlarda, oyuncu 3 bizim modele göre oyuncu 4 biraz daha yüksek sırada olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3c469-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="3c469-165">Çünkü oyuncu 3'ün oyuncu 1'e karşı kazandığı zafer, oyuncu 4'ün oyuncu 2'ye karşı kazandığı zaferden daha önemlidir – 1 oyuncunun 2'yi yendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3c469-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="3c469-166">Oyuncu 0 genel şampiyon!</span><span class="sxs-lookup"><span data-stu-id="3c469-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="3c469-167">Öğrenmeye devam edin</span><span class="sxs-lookup"><span data-stu-id="3c469-167">Keep learning</span></span>

<span data-ttu-id="3c469-168">İstatistiksel modeller tasarlamak kendi başına bir beceridir.</span><span class="sxs-lookup"><span data-stu-id="3c469-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="3c469-169">Microsoft Research Cambridge ekibi [ücretsiz](http://mbmlbook.com/)bir online kitap yazmıştır , hangi makaleye nazik bir giriş verir.</span><span class="sxs-lookup"><span data-stu-id="3c469-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="3c469-170">Bu kitabın Bölüm 3 daha ayrıntılı olarak TrueSkill modeli kapsar.</span><span class="sxs-lookup"><span data-stu-id="3c469-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="3c469-171">Bir kez aklınızda bir model var, Infer.NET web sitesinde [kapsamlı belgeleri](https://dotnet.github.io/infer/) kullanarak kod dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c469-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3c469-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3c469-172">Next steps</span></span>

<span data-ttu-id="3c469-173">Öğrenmeye devam etmek ve daha fazla örnek bulmak için Infer.NET GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="3c469-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3c469-174">dotnet/infer GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="3c469-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
