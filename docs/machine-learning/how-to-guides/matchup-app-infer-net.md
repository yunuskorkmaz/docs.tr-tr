---
title: Infer.NET ve probalistic programlama ile bir oyun eşleme listesi uygulaması oluşturma
description: Probalistic programlama ile Infer.NET TrueSkill basitleştirilmiş bir sürümünü temel alan bir oyun matchup listesi uygulaması oluşturmak için nasıl kullanılacağını keşfedin.
ms.date: 10/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ceeb0f43e03c7ce93f105498f44bf243eec86bbf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152480"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="7118c-103">Infer.NET ve olasılığa dayalı programlama ile bir oyun eşleme listesi uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7118c-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="7118c-104">Bu nasıl yapılır kılavuzunda Infer.NET kullanarak olasılığa dayalı programlama hakkında size öğretir.</span><span class="sxs-lookup"><span data-stu-id="7118c-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="7118c-105">Olasılığa dayalı programlama bir machine learning burada özel modelleri bilgisayar programları olarak ifade edilir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="7118c-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="7118c-106">Bu etki alanı bilgisini modellerindeki birleştirmek için izin verir ve makine öğrenimi sistemi daha yorumlanabilirinde yapar.</span><span class="sxs-lookup"><span data-stu-id="7118c-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="7118c-107">Ayrıca, çevrimiçi çıkarımı – yeni veriler ulaştıkça öğrenme işlemi destekler.</span><span class="sxs-lookup"><span data-stu-id="7118c-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="7118c-108">Microsoft Azure, Xbox ve Bing çeşitli ürünlerin Infer.NET kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7118c-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="7118c-109">Olasılığa dayalı programlama nedir?</span><span class="sxs-lookup"><span data-stu-id="7118c-109">What is probabilistic programming?</span></span>

<span data-ttu-id="7118c-110">Olasılığa dayalı programlama gerçek işlemlerin istatistiksel modeller oluşturmak sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="7118c-110">Probabilistic programming allows us to create statistical models of real-world processes.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="7118c-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7118c-111">Prerequisites</span></span>

- <span data-ttu-id="7118c-112">Yerel geliştirme ortamı Kurulumu</span><span class="sxs-lookup"><span data-stu-id="7118c-112">Local development environment setup</span></span>

  <span data-ttu-id="7118c-113">Bu nasıl yapılır kılavuzunda geliştirme için kullanabileceğiniz bir makine olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="7118c-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="7118c-114">.NET [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) öğretici Mac, PC ve Linux üzerinde yerel geliştirme ortamınızı ayarlama yönergeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7118c-114">The .NET [Get Started in 10 minutes](https://www.microsoft.com/net/core) tutorial has instructions for setting up your local development environment on Mac, PC, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="7118c-115">Uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7118c-115">Create your app</span></span>

1. <span data-ttu-id="7118c-116">Yeni bir komut istemi açın ve aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7118c-116">Open a new command prompt and run the following commands:</span></span>

```console
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="7118c-117">`dotnet` Komut oluşturur bir `new` uygulama türünün `console`.</span><span class="sxs-lookup"><span data-stu-id="7118c-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="7118c-118">`-o` Parametresi adlı bir dizin oluşturur `myApp` dosyaları uygulamanızı nerede depolanır ve gerekli ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="7118c-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="7118c-119">`cd myApp` Komutu, yeni oluşturulan uygulama dizine koyar.</span><span class="sxs-lookup"><span data-stu-id="7118c-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="7118c-120">Infer.NET paketini yükle</span><span class="sxs-lookup"><span data-stu-id="7118c-120">Install Infer.NET package</span></span>

<span data-ttu-id="7118c-121">Yüklemeniz gerekiyor Infer.NET kullanılacak `Microsoft.ML.Probabilistic.Compiler` paket.</span><span class="sxs-lookup"><span data-stu-id="7118c-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="7118c-122">Komut isteminde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7118c-122">In your command prompt, run the following command:</span></span>

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="7118c-123">Model tasarlama</span><span class="sxs-lookup"><span data-stu-id="7118c-123">Design your model</span></span>

<span data-ttu-id="7118c-124">Foosball eşleşen office içinde yürütülen ya da örnek örnek tablo tenis kullanır.</span><span class="sxs-lookup"><span data-stu-id="7118c-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="7118c-125">Katılımcılar ve her bir eşleştirmeyi sonucunu sahibiz.</span><span class="sxs-lookup"><span data-stu-id="7118c-125">We have the participants and outcome of each match.</span></span>  <span data-ttu-id="7118c-126">Bu verilerden oyuncunun becerileri çıkarsanacak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="7118c-126">We want to infer the player's skills from this data.</span></span> <span data-ttu-id="7118c-127">Normal olarak dağıtılmış bir görünmeyen becerisi her oyuncusu içeriyor ve performanslarını verilen eşleme bu beceri gürültülü sürümüdür varsayıyoruz.</span><span class="sxs-lookup"><span data-stu-id="7118c-127">We’ll assume that each player has a normally distributed latent skill and their performance in a given match is a noisy version of this skill.</span></span> <span data-ttu-id="7118c-128">Veri ödül performans kaybeden'ın performansı daha büyük olacak şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="7118c-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="7118c-129">Basitleştirilmiş bir sürümünü popüler budur [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, hangi takımları çizer ve diğer uzantılar da destekler.</span><span class="sxs-lookup"><span data-stu-id="7118c-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="7118c-130">Bir [Gelişmiş sürüm](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) bu modeli, en çok satan oyun başlıklarında Halo ve Gears, War matchmaking için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7118c-130">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="7118c-131">Kendi fark – becerileri belirsizliğin ölçüsü ile birlikte çıkarsanan player becerileri listelemek ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="7118c-131">We need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="7118c-132">*Oyun sonucu örnek veriler*</span><span class="sxs-lookup"><span data-stu-id="7118c-132">*Game result sample data*</span></span>

<span data-ttu-id="7118c-133">Oyun</span><span class="sxs-lookup"><span data-stu-id="7118c-133">Game</span></span> |<span data-ttu-id="7118c-134">Kazanan</span><span class="sxs-lookup"><span data-stu-id="7118c-134">Winner</span></span> | <span data-ttu-id="7118c-135">Kaybeden</span><span class="sxs-lookup"><span data-stu-id="7118c-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="7118c-136">1.</span><span class="sxs-lookup"><span data-stu-id="7118c-136">1</span></span> | <span data-ttu-id="7118c-137">Oynatıcı 0</span><span class="sxs-lookup"><span data-stu-id="7118c-137">Player 0</span></span> | <span data-ttu-id="7118c-138">Oynatıcı 1</span><span class="sxs-lookup"><span data-stu-id="7118c-138">Player 1</span></span>
 <span data-ttu-id="7118c-139">2</span><span class="sxs-lookup"><span data-stu-id="7118c-139">2</span></span> | <span data-ttu-id="7118c-140">Oynatıcı 0</span><span class="sxs-lookup"><span data-stu-id="7118c-140">Player 0</span></span> | <span data-ttu-id="7118c-141">Player 3</span><span class="sxs-lookup"><span data-stu-id="7118c-141">Player 3</span></span>
 <span data-ttu-id="7118c-142">3</span><span class="sxs-lookup"><span data-stu-id="7118c-142">3</span></span> | <span data-ttu-id="7118c-143">Oynatıcı 0</span><span class="sxs-lookup"><span data-stu-id="7118c-143">Player 0</span></span> | <span data-ttu-id="7118c-144">Player 4</span><span class="sxs-lookup"><span data-stu-id="7118c-144">Player 4</span></span>
 <span data-ttu-id="7118c-145">4</span><span class="sxs-lookup"><span data-stu-id="7118c-145">4</span></span> | <span data-ttu-id="7118c-146">Oynatıcı 1</span><span class="sxs-lookup"><span data-stu-id="7118c-146">Player 1</span></span> | <span data-ttu-id="7118c-147">Oynatıcı 2</span><span class="sxs-lookup"><span data-stu-id="7118c-147">Player 2</span></span>
 <span data-ttu-id="7118c-148">5</span><span class="sxs-lookup"><span data-stu-id="7118c-148">5</span></span> | <span data-ttu-id="7118c-149">Player 3</span><span class="sxs-lookup"><span data-stu-id="7118c-149">Player 3</span></span> | <span data-ttu-id="7118c-150">Oynatıcı 1</span><span class="sxs-lookup"><span data-stu-id="7118c-150">Player 1</span></span>
 <span data-ttu-id="7118c-151">6</span><span class="sxs-lookup"><span data-stu-id="7118c-151">6</span></span> | <span data-ttu-id="7118c-152">Player 4</span><span class="sxs-lookup"><span data-stu-id="7118c-152">Player 4</span></span> | <span data-ttu-id="7118c-153">Oynatıcı 2</span><span class="sxs-lookup"><span data-stu-id="7118c-153">Player 2</span></span>

<span data-ttu-id="7118c-154">Yakından ile örnek veriler, 3 ve 4 oyuncu bir win ve bir kaybı olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7118c-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="7118c-155">Olasılığa dayalı programlama kullanma gibi hangi sıralamasına Ara görelim.</span><span class="sxs-lookup"><span data-stu-id="7118c-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="7118c-156">Ayrıca bir oynatıcı sıfır bile office eşleşme liste sıfır bize geliştiriciler tabanlı olduğundan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7118c-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="7118c-157">Bazı kodlar yazma</span><span class="sxs-lookup"><span data-stu-id="7118c-157">Write some code</span></span>

<span data-ttu-id="7118c-158">Model tasarlanan bu API modelleme Infer.NET kullanarak olasılığa dayanan bir program olarak express zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="7118c-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="7118c-159">Açık `Program.cs` sık kullandığınız metin düzenleyicinizde ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7118c-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="7118c-160">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7118c-160">Run your app</span></span>

<span data-ttu-id="7118c-161">Komut isteminde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7118c-161">In your command prompt, run the following command:</span></span>

```console
dotnet run
```

## <a name="results"></a><span data-ttu-id="7118c-162">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="7118c-162">Results</span></span>

<span data-ttu-id="7118c-163">Sonuçlar aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7118c-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="7118c-164">Sonuçlarda oyuncu 3 4 oyuncu modelimizi göre biraz daha sıralayan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7118c-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="7118c-165">Oynatıcı 3 player 1 üzerinde tek tek oynatıcı 4 oyuncu 2 – üzerinden daha önemli çünkü 1 oyuncu vuruş player 2 unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7118c-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="7118c-166">Oynatıcı 0 Genel uzmanının sunuluyor</span><span class="sxs-lookup"><span data-stu-id="7118c-166">Player 0 is the overall champ!</span></span>  

## <a name="keep-learning"></a><span data-ttu-id="7118c-167">Öğrenme tutun</span><span class="sxs-lookup"><span data-stu-id="7118c-167">Keep learning</span></span>

<span data-ttu-id="7118c-168">İstatistiksel modelleri tasarlama, kendi kendine bir yetenektir.</span><span class="sxs-lookup"><span data-stu-id="7118c-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="7118c-169">Microsoft Research Cambridge takım yazılmış bir [ücretsiz çevrimiçi kitap](http://mbmlbook.com/), makalede size bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="7118c-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="7118c-170">Bölüm 3 kitabın TrueSkill modeli daha ayrıntılı bir şekilde anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7118c-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="7118c-171">Göz önünde bir modeli oluşturduktan sonra bu kodu kullanarak dönüştürebilirsiniz [dokümantasyonuna](https://dotnet.github.io/infer/) Infer.NET Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="7118c-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7118c-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7118c-172">Next steps</span></span>

<span data-ttu-id="7118c-173">Almaya devam etmek ve diğer örnekleri bulmak için Infer.NET GitHub havuzuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="7118c-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7118c-174">DotNet/Infer GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="7118c-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
