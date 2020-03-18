---
title: LINQ ile Çalışma
description: Bu öğretici, LINQ ile diziler oluşturmayı, LINQ sorgularında kullanım yöntemlerini yazmayı ve istekli ve tembel değerlendirmeyi birbirinden nasıl ayıracağınızı öğretir.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240021"
---
# <a name="work-with-language-integrated-query-linq"></a><span data-ttu-id="f7d21-103">Dil-Entegre Sorgu (LINQ) ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="f7d21-103">Work with Language-Integrated Query (LINQ)</span></span>

## <a name="introduction"></a><span data-ttu-id="f7d21-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="f7d21-104">Introduction</span></span>

<span data-ttu-id="f7d21-105">Bu öğretici size .NET Core ve C# dilinde ki özellikleri öğretir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="f7d21-106">Şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7d21-106">You’ll learn how to:</span></span>

- <span data-ttu-id="f7d21-107">LINQ ile diziler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f7d21-107">Generate sequences with LINQ.</span></span>
- <span data-ttu-id="f7d21-108">LINQ sorgularında kolayca kullanılabilen yazma yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f7d21-108">Write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="f7d21-109">Istekli ve tembel değerlendirme arasında ayrım.</span><span class="sxs-lookup"><span data-stu-id="f7d21-109">Distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="f7d21-110">Faro [shuffle:](https://en.wikipedia.org/wiki/Faro_shuffle)Herhangi bir sihirbaz temel becerilerinden birini gösteren bir uygulama oluşturarak bu teknikleri öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="f7d21-111">Kısaca, bir faro shuffle tam olarak ikiye bir kart destebölünmüş bir tekniktir, sonra shuffle orijinal güverte yeniden oluşturmak için her yarısından her bir kart interleaves.</span><span class="sxs-lookup"><span data-stu-id="f7d21-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="f7d21-112">Sihirbazlar bu tekniği kullanır, çünkü her kart her karıştırmadan sonra bilinen bir yerdedir ve sıra yinelenen bir desendir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="f7d21-113">Sizin amaçlarınız için, veri dizilerini manipüle etmek için açık yürekli bir bakış.</span><span class="sxs-lookup"><span data-stu-id="f7d21-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="f7d21-114">Oluşturacağınız uygulama bir kart destesi oluşturur ve ardından her seferinde sırayı yazarak bir dizi karışıklık gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-114">The application you'll build constructs a card deck and then performs a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="f7d21-115">Ayrıca güncelleştirilmiş siparişi orijinal siparişle karşılaştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="f7d21-116">Bu öğreticinin birden çok adımı vardır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="f7d21-117">Her adımdan sonra, uygulamayı çalıştırabilir ve ilerlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="f7d21-118">[Tamamlanan örneği](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/örnek GitHub deposunda da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="f7d21-119">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7d21-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f7d21-120">Prerequisites</span></span>

<span data-ttu-id="f7d21-121">.NET çekirdeğini çalıştırmak için makinenizi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="f7d21-122">Yükleme yönergelerini [.NET Çekirdek İndirme](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="f7d21-123">Bu uygulamayı Windows, Ubuntu Linux veya OS X'te veya Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-123">You can run this application on Windows, Ubuntu Linux, or OS X, or in a Docker container.</span></span> <span data-ttu-id="f7d21-124">En sevdiğiniz kod düzenleyicisini yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="f7d21-125">Aşağıdaki açıklamalar açık kaynak, çapraz platform düzenleyicisi [olan Visual Studio Code'u](https://code.visualstudio.com/) kullanabilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross-platform editor.</span></span> <span data-ttu-id="f7d21-126">Ancak, hangi araçları ile rahat kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="f7d21-127">Uygulamayı Oluştur</span><span class="sxs-lookup"><span data-stu-id="f7d21-127">Create the Application</span></span>

<span data-ttu-id="f7d21-128">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-128">The first step is to create a new application.</span></span> <span data-ttu-id="f7d21-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f7d21-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="f7d21-130">Bunu geçerli dizini yapın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-130">Make that the current directory.</span></span> <span data-ttu-id="f7d21-131">Komut istemine komut `dotnet new console` yazın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="f7d21-132">Bu, temel bir "Hello World" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="f7d21-133">Daha önce Hiç C# kullanmadıysanız, [bu öğretici](console-teleprompter.md) bir C# programının yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7d21-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="f7d21-134">Bunu okuyabilir ve linq hakkında daha fazla bilgi edinmek için buraya geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="create-the-data-set"></a><span data-ttu-id="f7d21-135">Veri Kümesini Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7d21-135">Create the Data Set</span></span>

<span data-ttu-id="f7d21-136">Başlamadan önce, aşağıdaki satırların aşağıdaki tarafından `Program.cs` `dotnet new console`oluşturulan dosyanın en üstünde olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="f7d21-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="f7d21-137">Bu üç satır`using` (deyimler) dosyanın en üstünde değilse, programımız derlemez.</span><span class="sxs-lookup"><span data-stu-id="f7d21-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="f7d21-138">Artık ihtiyacınız olan tüm referanslara sahip olduğunuza göre, bir kart destesini neyin oluşturduğunu düşünün.</span><span class="sxs-lookup"><span data-stu-id="f7d21-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="f7d21-139">Genellikle, bir deste iskambil kartı dört takım elbiseye sahiptir ve her takım elbisenin on üç değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="f7d21-140">Normalde, yarasa dan sağ `Card` kapalı bir sınıf oluşturma ve `Card` elle nesnelerin bir koleksiyon doldurma düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="f7d21-141">LINQ ile, bir kart destesi oluşturma yla başa çıkmanın her zamankinden daha kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="f7d21-142">Bir `Card` sınıf oluşturmak yerine, sırasıyla takım elbise ve sıralamaları temsil edecek iki dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="f7d21-143">Dereceleri ve dizeleri s olarak <xref:System.Collections.Generic.IEnumerable%601>uygun üretecek [*yineleyici yöntemleri*](../iterators.md#enumeration-sources-with-iterator-methods) gerçekten basit bir çift oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="f7d21-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="f7d21-144">Bunları dosyanızdaki `Program.cs` `Main` yöntemin altına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="f7d21-145">Bu iki yöntem, `yield return` çalışırken bir sıra oluşturmak için sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="f7d21-146">Derleyici, dizeleri istedikleri gibi <xref:System.Collections.Generic.IEnumerable%601> uygulayan ve üreten bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="f7d21-147">Şimdi, kart destesi oluşturmak için bu yineleyici yöntemlerikullanın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="f7d21-148">LINQ sorgusunu yöntemimize `Main` yerleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="f7d21-149">İşte bir bakış:</span><span class="sxs-lookup"><span data-stu-id="f7d21-149">Here's a look at it:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

<span data-ttu-id="f7d21-150">Birden `from` çok yan <xref:System.Linq.Enumerable.SelectMany%2A>tümce, ilk dizideki her öğeyi ikinci sırada her öğeyle birleştirerek tek bir sıra oluşturan bir , üretir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="f7d21-151">Emir bizim amaçlarımız için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-151">The order is important for our purposes.</span></span> <span data-ttu-id="f7d21-152">İlk kaynak dizisindeki ilk öğe (Suit) ikinci dizideki (Sıralar) her öğeyle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="f7d21-153">Bu ilk takım tüm on üç kart üretir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="f7d21-154">Bu işlem, ilk sırada (Suits) her öğe ile tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="f7d21-155">Sonuç, takım elbiseler tarafından sipariş edilen bir kart destesi ve ardından değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="f7d21-156">LinQ'unuzu yukarıda kullanılan sorgu sözdizimine yazmayı veya bunun yerine yöntem sözdizimini kullanmayı seçseniz de, bir sözdiziminden diğerine geçmenin her zaman mümkün olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="f7d21-157">Sorgu sözdiziminde yazılan yukarıdaki sorgu yöntem sözdiziminde şöyle yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="f7d21-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="f7d21-158">Derleyici, sorgu sözdizimi ile yazılmış LINQ deyimlerini eşdeğer yöntem çağrı sözdizimine çevirir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="f7d21-159">Bu nedenle, sözdizimi seçiminiz ne olursa olsun, sorgunun iki sürümü aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="f7d21-160">Durumunuz için en iyi sonucu seçin: örneğin, bazı üyelerin yöntem sözdizimi ile ilgili zorluk yaşadığı bir takımda çalışıyorsanız, sorgu sözdizimini kullanmayı tercih etmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="f7d21-161">Devam edin ve bu noktada oluşturduğun örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="f7d21-162">52 kartın tümlerini destede gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="f7d21-163">Bu örneği bir hata ayıklama altında çalıştırmayı ve `Suits()` `Ranks()` yöntemlerin nasıl yürütüldünlerini gözlemlemeniz çok yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="f7d21-164">Her dizideki her dizenin yalnızca gerektiği gibi oluşturulduğunu açıkça görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Uygulamanın 52 kart yazdığını gösteren bir konsol penceresi.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a><span data-ttu-id="f7d21-166">Siparişi Manipüle Edin</span><span class="sxs-lookup"><span data-stu-id="f7d21-166">Manipulate the Order</span></span>

<span data-ttu-id="f7d21-167">Sonra, destedeki kartları nasıl karıştıracağınız üzerine odaklanın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="f7d21-168">Herhangi bir iyi shuffle ilk adım iki güverte bölmektir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="f7d21-169">LINQ API'lerinin bir parçası olan yöntemler <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemler bu özelliği sizin için sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7d21-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="f7d21-170">Onları döngünün `foreach` altına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="f7d21-170">Place them underneath the `foreach` loop:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

<span data-ttu-id="f7d21-171">Ancak, standart kitaplıkta yararlanabileceğiniz bir karıştırma yöntemi yoktur, bu nedenle kendi kitaplığınızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="f7d21-172">Oluşturacağınız karıştırma yöntemi, LINQ tabanlı programlarda kullanacağınız çeşitli teknikleri gösterir, böylece bu işlemin her bölümü adım adım açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="f7d21-173">LINQ sorgularından geri <xref:System.Collections.Generic.IEnumerable%601> alacağınız ile nasıl etkileşimde bulunacağınız [için, uzantı yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)adı verilen bazı özel yöntemler yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="f7d21-174">Kısaca, uzantı yöntemi, işlevsellik eklemek istediğiniz özgün türü değiştirmek zorunda kalmadan zaten varolan bir türe yeni işlevler ekleyen özel amaçlı statik bir *yöntemdir.*</span><span class="sxs-lookup"><span data-stu-id="f7d21-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="f7d21-175">Programınıza `Extensions.cs`yeni bir *statik* sınıf dosyası ekleyerek uzantı yöntemlerinize yeni bir ev verin ve ardından ilk uzantı yöntemini oluşturmaya başlayın:</span><span class="sxs-lookup"><span data-stu-id="f7d21-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

<span data-ttu-id="f7d21-176">Bir an için yöntem imzabak, özellikle parametreleri:</span><span class="sxs-lookup"><span data-stu-id="f7d21-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="f7d21-177">Yönteme ilk bağımsız `this` değişkende değiştiricinin ekini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="f7d21-178">Bu, yöntemi ilk bağımsız değişken türünün bir üyesi yöntemiymiş gibi adlandırdığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="f7d21-179">Bu yöntem bildirimi, giriş ve çıkış türlerinin bulunduğu `IEnumerable<T>`standart bir deyim de izler.</span><span class="sxs-lookup"><span data-stu-id="f7d21-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="f7d21-180">Bu uygulama, linq yöntemlerinin daha karmaşık sorgular gerçekleştirmek için birbirine zincirlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7d21-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="f7d21-181">Doğal olarak, desteyi ikiye böldüğün için bu yarılara birlikte katılman gerekecek.</span><span class="sxs-lookup"><span data-stu-id="f7d21-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="f7d21-182">Kod olarak, bu, elde <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> *`interleaving`* ettiğiniz her iki diziyi de, öğeleri ve bir sırayı şu anda karıştırDığınız kart destenizi sıralaacağınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="f7d21-183">İki diziyle çalışan bir LINQ yöntemi yazmak, <xref:System.Collections.Generic.IEnumerable%601> nasıl çalıştığını anlamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="f7d21-184"><xref:System.Collections.Generic.IEnumerable%601> Arabirimin tek bir <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>yöntemi vardır: .</span><span class="sxs-lookup"><span data-stu-id="f7d21-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="f7d21-185">Döndürülen <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> nesnenin bir sonraki öğeye taşımak için bir yöntemi ve dizideki geçerli öğeyi alan bir özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="f7d21-186">Bu iki üyeyi koleksiyonu sayısallandırmak ve öğeleri döndürmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="f7d21-187">Bu Interleave yöntemi bir yineleyici yöntemi olacaktır, bu nedenle bir koleksiyon oluşturmak ve koleksiyonu `yield return` döndürmek yerine, yukarıda gösterilen sözdizimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="f7d21-188">İşte bu yöntemin uygulanması:</span><span class="sxs-lookup"><span data-stu-id="f7d21-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="f7d21-189">Artık bu yöntemi yazdığınız için yönteme `Main` geri dön ve desteyi bir kez karıştırın:</span><span class="sxs-lookup"><span data-stu-id="f7d21-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="f7d21-190">Karşılaştırmalar</span><span class="sxs-lookup"><span data-stu-id="f7d21-190">Comparisons</span></span>

<span data-ttu-id="f7d21-191">Desteyi orijinal düzenine geri ayarlamak için kaç değişiklik gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="f7d21-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="f7d21-192">Öğrenmek için, iki dizinin eşit olup olmadığını belirleyen bir yöntem yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="f7d21-193">Bu yönteme sahip olduktan sonra, desteyi bir döngüye karıştıran kodu yerleştirmeniz ve destenin ne zaman düzene geri döndüğünü kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="f7d21-194">İki dizinin eşit olup olmadığını belirlemek için bir yöntem yazmak basit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="f7d21-195">Desteyi karıştırmak için yazdığın yönteme benzer bir yapı.</span><span class="sxs-lookup"><span data-stu-id="f7d21-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="f7d21-196">Yalnızca bu kez, `yield return`her öğeyi almak yerine, her dizinin eşleşen öğelerini karşılaştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="f7d21-197">Tüm sıra numaralandırıldığında, her öğe eşleşirse, diziler aynıdır:</span><span class="sxs-lookup"><span data-stu-id="f7d21-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="f7d21-198">Bu ikinci bir LINQ deyimini gösterir: terminal yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f7d21-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="f7d21-199">Giriş olarak bir sıra alırlar (veya bu durumda, iki dizi) ve tek bir skaler değer döndürerler.</span><span class="sxs-lookup"><span data-stu-id="f7d21-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="f7d21-200">Terminal yöntemlerini kullanırken, linq sorgusu için bir yöntem zincirinde her zaman son yöntemdir, dolayısıyla "terminal" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="f7d21-201">Destenin orijinal sırasına ne zaman geri döndüğünü belirlemek için kullandığınızda bunu iş başında görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="f7d21-202">Karıştırma kodunu bir döngüye koyun ve yöntemi uygulayarak dizi orijinal sırasına geri döndüğünde durdurun. `SequenceEquals()`</span><span class="sxs-lookup"><span data-stu-id="f7d21-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="f7d21-203">Bir dizi yerine tek bir değer döndürdüğünden, her sorguda her zaman son yöntem olacağını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7d21-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="f7d21-204">Şimdiye kadar var olan kodu çalıştırın ve her shuffle'da destenin nasıl yeniden düzenlediğini göz önünde virde edin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="f7d21-205">8 karışıklıktan (yap döngüsüyinelemeleri) sonra, güverte, başlangıç LINQ sorgusundan ilk oluşturduğunuzda olduğu orijinal yapılandırmaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="f7d21-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="f7d21-206">İyileştirmeler</span><span class="sxs-lookup"><span data-stu-id="f7d21-206">Optimizations</span></span>

<span data-ttu-id="f7d21-207">Şimdiye kadar oluşturabileceğiniz örnek, üst ve alt kartların her çalıştırmada aynı kaldığı bir *dış karıştırma*işlemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="f7d21-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="f7d21-208">Bir değişiklik yapalım: 52 kartın tamamının yerini değiştirdiği bir *karışık* lık kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="f7d21-209">Bir karıştırma için, alt yarısında ilk kart destedeki ilk kart olur, böylece deste interleave.</span><span class="sxs-lookup"><span data-stu-id="f7d21-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="f7d21-210">Bu da üst yarıdaki son kartın alt kart olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="f7d21-211">Bu, tekil bir kod satırında yapılan basit bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="f7d21-212">Konumlarını değiştirerek geçerli karıştırma <xref:System.Linq.Enumerable.Take%2A> sorgusunu güncelleştirin ve <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7d21-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="f7d21-213">Bu, destenin üst ve alt yarısının sırasını değiştirir:</span><span class="sxs-lookup"><span data-stu-id="f7d21-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="f7d21-214">Programı yeniden çalıştırDığınızda, destenin kendisini yeniden sipariş etmesi için 52 yineleme gerektiğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="f7d21-215">Ayrıca, program çalışmaya devam ettikçe bazı ciddi performans bozulmaları fark etmeye başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="f7d21-216">Bunun birkaç nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-216">There are a number of reasons for this.</span></span> <span data-ttu-id="f7d21-217">Bu performans düşüşünün başlıca nedenlerinden biriyle başa çıkabilirsiniz: [*tembel değerlendirmenin*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)verimsiz kullanımı.</span><span class="sxs-lookup"><span data-stu-id="f7d21-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="f7d21-218">Kısaca, tembel değerlendirme, bir deyimin değerinin gerekli olana kadar değerlendirilmesinin gerçekleştirilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="f7d21-219">LINQ sorguları tembelce değerlendirilen ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="f7d21-220">Diziler yalnızca öğeler istendiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="f7d21-221">Genellikle, bu LINQ büyük bir yararı' s.</span><span class="sxs-lookup"><span data-stu-id="f7d21-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="f7d21-222">Ancak, bu program gibi bir kullanımda, bu yürütme süresi üstel büyüme neden olur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="f7d21-223">Orijinal desteyi LINQ sorgusu kullanarak oluşturduğumuzu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="f7d21-224">Her karıştırma, önceki güvertede üç LINQ sorgusu gerçekleştirerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="f7d21-225">Tüm bunlar tembelce yapılır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-225">All these are performed lazily.</span></span> <span data-ttu-id="f7d21-226">Bu aynı zamanda, dizi her istendiğinde yeniden gerçekleştirildikleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="f7d21-227">52. yinelemeye geldiğinizde orijinal güverteyi birçok kez yenilin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="f7d21-228">Bu davranışı göstermek için bir günlük yazalım.</span><span class="sxs-lookup"><span data-stu-id="f7d21-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="f7d21-229">O zaman tamir edeceksin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-229">Then, you'll fix it.</span></span>

<span data-ttu-id="f7d21-230">Dosyanızda `Extensions.cs` aşağıdaki yöntemi yazın veya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="f7d21-231">Bu uzantı yöntemi, proje `debug.log` dizininizde adı verilen yeni bir dosya oluşturur ve günlük dosyasına şu anda yürütülmekte olan sorguyu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f7d21-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="f7d21-232">Bu uzantı yöntemi, sorgunun yürütüldettiğini işaretlemek için herhangi bir sorguya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="f7d21-233">Altında `File`kırmızı bir dalgalı göreceksiniz, yani öyle bir şey yok.</span><span class="sxs-lookup"><span data-stu-id="f7d21-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="f7d21-234">Derleyici ne `File` olduğunu bilmediği için derleme yapmaz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="f7d21-235">Bu sorunu çözmek için, aşağıdaki kod satırını aşağıdaki ilk `Extensions.cs`satırın altına eklediğinizden emin olun:</span><span class="sxs-lookup"><span data-stu-id="f7d21-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="f7d21-236">Bu sorunu çözmek gerekir ve kırmızı hata kaybolur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="f7d21-237">Ardından, günlük iletisi ile her sorgunun tanımını enstrüman:</span><span class="sxs-lookup"><span data-stu-id="f7d21-237">Next, instrument the definition of each query with a log message:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="f7d21-238">Bir sorguya her erişimede günlüğe kaydetmediğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="f7d21-239">Yalnızca özgün sorguyu oluşturduğunuzda oturum açarsınız.</span><span class="sxs-lookup"><span data-stu-id="f7d21-239">You log only when you create the original query.</span></span> <span data-ttu-id="f7d21-240">Program hala çalıştırmak için uzun bir zaman alır, ama şimdi neden görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="f7d21-241">Giriş açıkken in shuffle çalıştıran sabrınız biterse, çıkış shuffle'ına geri geçin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="f7d21-242">Hala tembel değerlendirme etkilerini göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="f7d21-243">Bir çalıştırmada, tüm değer ve takım elbise oluşturma dahil olmak üzere 2592 sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="f7d21-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="f7d21-244">Yaptığınız yürütme sayısını azaltmak için burada kodun performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="f7d21-245">Yapabileceğiniz basit bir düzeltme, kart destesini oluşturan orijinal LINQ sorgusunun sonuçlarını *önbelleğe* almaktır.</span><span class="sxs-lookup"><span data-stu-id="f7d21-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="f7d21-246">Şu anda, do-while döngüsü bir yinelemeden geçse, kart destesini yeniden oluşturup her seferinde yeniden karıştırarak sorguları tekrar tekrar yürütesiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d21-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="f7d21-247">Kart destesini önbelleğe almak için LINQ <xref:System.Linq.Enumerable.ToArray%2A> <xref:System.Linq.Enumerable.ToList%2A>yöntemlerinden ve; Sorguları eklediğinizde, onlara söylediğiniz eylemleri gerçekleştirirler, ancak şimdi aramayı seçtiğiniz yönteme bağlı olarak sonuçları bir dizi veya liste halinde depolarlar.</span><span class="sxs-lookup"><span data-stu-id="f7d21-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="f7d21-248">Linq yöntemini <xref:System.Linq.Enumerable.ToArray%2A> her iki sorguya de ekleyip programı yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f7d21-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="f7d21-249">Şimdi çıkış karışıklığı 30 sorguya düştü.</span><span class="sxs-lookup"><span data-stu-id="f7d21-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="f7d21-250">In shuffle ile yeniden çalıştırın ve benzer iyileştirmeler görürsünüz: şimdi 162 sorguları yürütür.</span><span class="sxs-lookup"><span data-stu-id="f7d21-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="f7d21-251">Bu örneğin, tembel değerlendirmenin performans güçlüklerine neden olabileceği kullanım örneklerini vurgulamak için **tasarlandığına** dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="f7d21-252">Tembel değerlendirmenin kod performansını nerede etkileebileceğini görmek önemli olsa da, tüm sorguların hevesle çalışmaması gerektiğini anlamak da aynı derecede önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="f7d21-253">Kullanmadan maruz kalmanızı <xref:System.Linq.Enumerable.ToArray%2A> sağlar, çünkü kart destesinin her yeni düzenlemesi önceki düzenlemeden oluşturulmuştür.</span><span class="sxs-lookup"><span data-stu-id="f7d21-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="f7d21-254">Tembel değerlendirme kullanarak her yeni güverte yapılandırması orijinal güverteden inşa edilir `startingDeck`anlamına gelir, hatta inşa kodu yürütme .</span><span class="sxs-lookup"><span data-stu-id="f7d21-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="f7d21-255">Bu da büyük miktarda ekstra çalışmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="f7d21-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="f7d21-256">Uygulamada, bazı algoritmalar istekli değerlendirme kullanarak iyi çalışır ve diğerleri tembel değerlendirme kullanarak iyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f7d21-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="f7d21-257">Günlük kullanım için, veri kaynağı ayrı bir işlem olduğunda, veritabanı altyapısı gibi tembel değerlendirme genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="f7d21-258">Veritabanları için, tembel değerlendirme daha karmaşık sorguları veritabanı işlemine yalnızca bir gidiş-dönüş yürütmek ve kodunuzun geri dönmek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="f7d21-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="f7d21-259">LINQ ister tembel ister istekli değerlendirmeyi kullanmayı seçseniz de esnektir, bu nedenle süreçlerinizi ölçün ve size en iyi performansı veren değerlendirme türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="f7d21-260">Sonuç</span><span class="sxs-lookup"><span data-stu-id="f7d21-260">Conclusion</span></span>

<span data-ttu-id="f7d21-261">Bu projede şunları ele alasınız:</span><span class="sxs-lookup"><span data-stu-id="f7d21-261">In this project, you covered:</span></span>

- <span data-ttu-id="f7d21-262">verileri anlamlı bir sıraya toplamak için LINQ sorgularını kullanma</span><span class="sxs-lookup"><span data-stu-id="f7d21-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="f7d21-263">LINQ sorgularına kendi özel işlevselliğimizi eklemek için Uzantı yöntemleri yazma</span><span class="sxs-lookup"><span data-stu-id="f7d21-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="f7d21-264">kurallarımızda LINQ sorgularımızın bozulmuş hız gibi performans sorunlarıyla karşılaşabileceği alanları bulma</span><span class="sxs-lookup"><span data-stu-id="f7d21-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="f7d21-265">LINQ sorguları ve sorgu performansı üzerindeki etkileri açısından tembel ve istekli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f7d21-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="f7d21-266">Linq dışında, sihirbazların kart numaraları için kullandıkları bir teknik hakkında biraz bilgi edindin.</span><span class="sxs-lookup"><span data-stu-id="f7d21-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="f7d21-267">Sihirbazlar Faro karışıklığını kullanırlar çünkü destedeki her kartın nereye gittiğini kontrol edebilirler.</span><span class="sxs-lookup"><span data-stu-id="f7d21-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="f7d21-268">Artık bildiğine göre, herkes için bunu mahvetme!</span><span class="sxs-lookup"><span data-stu-id="f7d21-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="f7d21-269">LINQ hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="f7d21-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="f7d21-270">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f7d21-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f7d21-271">LINQ'ye Giriş</span><span class="sxs-lookup"><span data-stu-id="f7d21-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f7d21-272">Temel LINQ Sorgu İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d21-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [<span data-ttu-id="f7d21-273">LINQ ile Veri Dönüşümleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d21-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [<span data-ttu-id="f7d21-274">LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d21-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [<span data-ttu-id="f7d21-275">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f7d21-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
