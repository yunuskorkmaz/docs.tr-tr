---
title: LINQ ile Çalışma
description: Bu öğreticide LINQ, LINQ sorgularında kullanılmak üzere yazma yöntemleriyle diziler oluşturma ve Eager ile yavaş değerlendirme arasında ayrım yapma öğretilir.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 72bb7475fc6b18650e0870bf99c4b8ddbac3ec9f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926614"
---
# <a name="working-with-linq"></a><span data-ttu-id="37bf5-103">LINQ ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="37bf5-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="37bf5-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="37bf5-104">Introduction</span></span>

<span data-ttu-id="37bf5-105">Bu öğretici, .NET Core ve C# dil özelliklerini size öğretir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="37bf5-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="37bf5-106">You’ll learn:</span></span>

- <span data-ttu-id="37bf5-107">LINQ ile diziler oluşturma.</span><span class="sxs-lookup"><span data-stu-id="37bf5-107">How to generate sequences with LINQ.</span></span>
- <span data-ttu-id="37bf5-108">LINQ sorgularında kolayca kullanılabilecek yöntemler yazma.</span><span class="sxs-lookup"><span data-stu-id="37bf5-108">How to write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="37bf5-109">Eager ve geç değerlendirme arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="37bf5-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="37bf5-110">Herhangi bir Magician temel becerilerinden birini gösteren bir uygulama oluşturarak bu teknikleri öğrenirsiniz: [Faro karışık](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="37bf5-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="37bf5-111">Kısaca, bir kağıt destesi yarısını tamamen yarıya böldüğünüz bir tekniktir, sonra da orijinal destesi yeniden derlemek için her bir yarısını her bir karmadan karıştırın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="37bf5-112">Magicians bu tekniği, her kart her karıştırmadan sonra bilinen bir konumda olduğundan ve sipariş yinelenen bir düzen olduğundan kullanın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="37bf5-113">Amacınıza uygun olarak, veri dizilerini işlemek için bir hafif göz atın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="37bf5-114">Oluşturacağınız uygulama bir kart destesi oluşturacak ve sonra her seferinde sırayı yazarak bir dizi karışık olarak bir sıra gerçekleştirecek.</span><span class="sxs-lookup"><span data-stu-id="37bf5-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="37bf5-115">Ayrıca, güncelleştirilmiş siparişi orijinal siparişle karşılaştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="37bf5-116">Bu öğreticide birden çok adım vardır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="37bf5-117">Her adımdan sonra, uygulamayı çalıştırabilir ve ilerleme durumunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="37bf5-118">Ayrıca, DotNet/Samples GitHub deposunda [Tamamlanan örneği](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="37bf5-119">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="37bf5-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37bf5-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="37bf5-120">Prerequisites</span></span>

<span data-ttu-id="37bf5-121">.NET Core 'u çalıştırmak için makinenizi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="37bf5-122">Yükleme yönergelerini [.NET Core indirme](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="37bf5-123">Bu uygulamayı Windows, Ubuntu Linux, OS X veya bir Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="37bf5-124">En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="37bf5-125">Aşağıdaki açıklamalar açık kaynaklı, platformlar arası düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="37bf5-126">Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="37bf5-127">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="37bf5-127">Create the Application</span></span>

<span data-ttu-id="37bf5-128">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-128">The first step is to create a new application.</span></span> <span data-ttu-id="37bf5-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37bf5-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="37bf5-130">Geçerli dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37bf5-130">Make that the current directory.</span></span> <span data-ttu-id="37bf5-131">`dotnet new console` Komutu komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="37bf5-132">Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="37bf5-133">Daha önce hiç kullanmadıysanız C# , [Bu öğretici](console-teleprompter.md) bir C# programın yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="37bf5-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="37bf5-134">Bunu okuyabilir ve sonra LINQ hakkında daha fazla bilgi edinmek için buraya dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="creating-the-data-set"></a><span data-ttu-id="37bf5-135">Veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="37bf5-135">Creating the Data Set</span></span>

<span data-ttu-id="37bf5-136">Başlamadan önce, aşağıdaki satırların tarafından `Program.cs` `dotnet new console`oluşturulan dosyanın en üstünde olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="37bf5-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="37bf5-137">Bu üç çizgi (`using` deyimler) dosyanın en üstünde değilse, programımız derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="37bf5-138">İhtiyacınız olan tüm başvurulara sahip olduğunuza göre, kart destesi ne olduğunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="37bf5-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="37bf5-139">Yaygın olarak, kart oynamaya yönelik bir deste dört cins içerir ve her cinsten on yedi değer vardır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="37bf5-140">Normalde, bir sınıfı doğrudan bir `Card` sınıf oluşturmayı ve bir `Card` nesne koleksiyonunu el ile doldurmayı düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="37bf5-141">LINQ ile, kart destesi oluşturma konusunda olağan yollardan daha kısa bir işlem yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="37bf5-142">`Card` Sınıf oluşturmak yerine, sırasıyla cins ve dereceleri temsil eden iki sıra oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="37bf5-143">Dizeleri ve <xref:System.Collections.Generic.IEnumerable%601>bu nesnelerin her birini oluşturacak olan bir çok basit [*Yineleyici yöntemleri*](../iterators.md#enumeration-sources-with-iterator-methods) oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="37bf5-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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

<span data-ttu-id="37bf5-144">Bunları `Main` `Program.cs` dosyanıza bu yöntemin altına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="37bf5-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="37bf5-145">Bu iki yöntem her ikisi de `yield return` çalıştıkları sırada bir sıra oluşturmak için söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="37bf5-146">Derleyici, istenen bir nesne oluşturur <xref:System.Collections.Generic.IEnumerable%601> ve bu sırada dizelerin dizisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="37bf5-147">Şimdi, kart destesi oluşturmak için bu yineleyici yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="37bf5-148">LINQ sorgusunu kendi yönteemiz `Main` olacak şekilde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="37bf5-149">İşte buna bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="37bf5-149">Here's a look at it:</span></span>

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

<span data-ttu-id="37bf5-150">Birden çok `from` yan tümce, <xref:System.Linq.Enumerable.SelectMany%2A>ikinci dizideki her öğe ile ilk dizideki her öğeyi birleştiren tek bir sıra oluşturan bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="37bf5-151">Sıra, amacınız açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-151">The order is important for our purposes.</span></span> <span data-ttu-id="37bf5-152">İlk kaynak dizideki (cins) ilk öğe, ikinci dizideki her öğe (Rütler) ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="37bf5-153">Bu, birinci cins 'in tüm üçüncü dört kartını üretir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="37bf5-154">Bu işlem, ilk dizideki (cins) her öğe ile yinelenir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="37bf5-155">Nihai sonuç, cinsler tarafından, ardından değerler tarafından sıralanan kartların bir destesi.</span><span class="sxs-lookup"><span data-stu-id="37bf5-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="37bf5-156">Yukarıda kullanılan sorgu söz diziminde LINQ 'nizi yazmayı veya bunun yerine Yöntem sözdizimini kullanmayı tercih etmeksizin, bir sözdizimi formundan diğerine gitmeniz her zaman mümkündür.</span><span class="sxs-lookup"><span data-stu-id="37bf5-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="37bf5-157">Sorgu sözdiziminde yazılan yukarıdaki sorgu yöntem sözdiziminde şöyle yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="37bf5-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="37bf5-158">Derleyici, sorgu söz dizimi ile yazılan LINQ deyimlerini eşdeğer Yöntem çağrısı sözdizimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="37bf5-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="37bf5-159">Bu nedenle, söz dizimi seçiminizden bağımsız olarak, sorgunun iki sürümü aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="37bf5-160">Hangi sözdiziminin durumunuz için en iyi şekilde çalıştığını seçin: Örneğin, bir ekip içinde çalışıyorsanız, bazı üyelerin Yöntem sözdizimi konusunda zorluk yaşıyorsanız, sorgu söz dizimini kullanmayı tercih edin.</span><span class="sxs-lookup"><span data-stu-id="37bf5-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="37bf5-161">Devam edin ve bu noktada derlediğiniz örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="37bf5-162">Bu, destedeki tüm 52 kartları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="37bf5-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="37bf5-163">`Suits()` Ve`Ranks()` yöntemlerinin nasıl yürütüleceğini gözlemlemek için bu örneği bir hata ayıklayıcı altında çalıştırmanın çok yararlı olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="37bf5-164">Her bir dizinin her bir dizesinin yalnızca gerektiğinde oluşturulduğunu açıkça görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![52 kart yazan uygulamayı gösteren bir konsol penceresi.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="37bf5-166">Siparişi düzenleme</span><span class="sxs-lookup"><span data-stu-id="37bf5-166">Manipulating the Order</span></span>

<span data-ttu-id="37bf5-167">Ardından, destedeki kartları nasıl karıştığınıza odaklanın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="37bf5-168">Her iyi karışmaya yönelik ilk adım, desteyi ikiye bölmenizde yarar vardır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="37bf5-169">LINQ API <xref:System.Linq.Enumerable.Skip%2A> 'lerinin parçası olan veyöntemleri,buözelliğisiziniçinsağlar.<xref:System.Linq.Enumerable.Take%2A></span><span class="sxs-lookup"><span data-stu-id="37bf5-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="37bf5-170">Bunları `foreach` döngünün altına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="37bf5-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="37bf5-171">Ancak, standart kitaplıkta avantajlarından yararlanmak için bir karıştırma yöntemi yoktur, bu nedenle kendi kodunuzu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="37bf5-172">Oluşturmakta olduğunuz karıştırma yöntemi, LINQ tabanlı programlarla birlikte kullanacağınız birkaç tekniği gösterir. bu nedenle, bu işlemin her bir bölümü adımlarda açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="37bf5-173">İle nasıl etkileşim kurabileceğine ilişkin <xref:System.Collections.Generic.IEnumerable%601> bazı işlevler eklemek için LINQ sorgularından geri dönebilirsiniz, [Uzantı yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)adlı bazı özel tür yöntemler yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="37bf5-174">Kısaca, bir genişletme yöntemi, işlevselliği eklemek istediğiniz orijinal türü değiştirmek zorunda kalmadan, zaten var olan bir türe yeni işlevsellik ekleyen özel amaçlı *statik bir yöntemdir* .</span><span class="sxs-lookup"><span data-stu-id="37bf5-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="37bf5-175">Adlı`Extensions.cs`programınıza yeni bir *statik* sınıf dosyası ekleyerek ve sonra ilk uzantı yöntemini oluşturmaya başlamak için uzantı yöntemlerinizi yeni bir giriş yapın:</span><span class="sxs-lookup"><span data-stu-id="37bf5-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

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

<span data-ttu-id="37bf5-176">Yöntem imzasına bir süre için bakın, özellikle Parametreler:</span><span class="sxs-lookup"><span data-stu-id="37bf5-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="37bf5-177">Metodun ilk bağımsız değişkenine `this` değiştiricinin eklenmesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="37bf5-178">Bu, yöntemi ilk bağımsız değişkenin türünün bir Member yöntemi gibi çağırmış olmanız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="37bf5-179">Bu yöntem bildirimi Ayrıca, giriş ve çıkış türlerinin `IEnumerable<T>`bulunduğu standart bir IOM 'yi izler.</span><span class="sxs-lookup"><span data-stu-id="37bf5-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="37bf5-180">Bu uygulama, LINQ yöntemlerinin daha karmaşık sorgular gerçekleştirmek için birlikte zincirde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="37bf5-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="37bf5-181">Doğal olarak, desteyi halele böldüğünüz için bu kilitlenenlere birlikte katılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="37bf5-182">Kod içinde bu, hem bir kez, <xref:System.Linq.Enumerable.Take%2A> *`interleaving`* hem de tek bir sıra oluşturduğunuz her iki diziyi <xref:System.Linq.Enumerable.Skip%2A> de numaralandırdığınız anlamına gelir: şimdi karışık kart destesi.</span><span class="sxs-lookup"><span data-stu-id="37bf5-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="37bf5-183">İki sıra ile çalışacak bir LINQ yöntemi yazmak için nasıl <xref:System.Collections.Generic.IEnumerable%601> çalıştığını anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="37bf5-184">Arabirimin bir yöntemi vardır: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="37bf5-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="37bf5-185">Tarafından <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> döndürülen nesne bir sonraki öğeye ve dizideki geçerli öğeyi alan bir özelliğe sahip bir yönteme sahip.</span><span class="sxs-lookup"><span data-stu-id="37bf5-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="37bf5-186">Bu iki üyeyi, koleksiyonu numaralandırmak ve öğeleri döndürmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="37bf5-187">Bu ayırma yöntemi bir yineleyici yöntemi olacak, bu nedenle bir koleksiyon oluşturmak ve koleksiyonu döndürmek yerine yukarıda gösterilen `yield return` söz dizimini kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="37bf5-188">Bu yöntemin uygulanması aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="37bf5-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="37bf5-189">Bu yöntemi yazdıktan sonra, `Main` yönteme dönün ve destesi bir kez karışın:</span><span class="sxs-lookup"><span data-stu-id="37bf5-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="37bf5-190">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="37bf5-190">Comparisons</span></span>

<span data-ttu-id="37bf5-191">Destesi orijinal sıralarına geri ayarlamak için kaç tane karışık?</span><span class="sxs-lookup"><span data-stu-id="37bf5-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="37bf5-192">Bunu öğrenmek için, iki sıranın eşit olup olmadığını belirleyen bir yöntem yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="37bf5-193">Bu yöntemi aldıktan sonra, destesi bir döngüyle karışık olarak sunan kodu yerleştirmeniz ve destenin sırasıyla ne zaman geri olduğunu kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="37bf5-194">İki sıranın eşit olup olmadığını anlamak için bir yöntem yazmak basit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="37bf5-195">Bu, destesi karıştırmak için yazdığınız yöntemin benzer bir yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="37bf5-196">Her öğe yerine `yield return`yalnızca bu kez her bir sıranın eşleşen öğelerini karşılaştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="37bf5-197">Tüm sıra numaralandırılmışsa, her öğe eşleşiyorsa, sıralar aynıdır:</span><span class="sxs-lookup"><span data-stu-id="37bf5-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="37bf5-198">Bu, ikinci bir LINQ deyimidir: Terminal yöntemlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="37bf5-199">Bunlar girdi olarak bir sıra alır (veya bu durumda iki dizi) ve tek bir skaler değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="37bf5-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="37bf5-200">Terminal yöntemleri kullanılırken, her zaman bir LINQ sorgusunun Yöntem zincirindeki son yöntem ve bu nedenle "Terminal" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="37bf5-201">Bu işlemi, deste 'nın orijinal düzeninde ne zaman geri yükleneceğini tespit etmek için kullandığınızda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="37bf5-202">Karışık kodu bir döngü içine koyun ve `SequenceEquals()` yöntemi uygulayarak sıra özgün sırasına geri döndüğünüzde durur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="37bf5-203">Bir dizi yerine tek bir değer döndürdüğünden, her sorguda her zaman son yöntem olacağını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="37bf5-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="37bf5-204">Şimdiye kadar aldığınız kodu çalıştırın ve her bir karıştırmadan destesi nasıl yeniden bir şekilde yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="37bf5-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="37bf5-205">8 karışık (do-while döngüsünün yinelemesi) sonrasında, deste başlangıç LINQ sorgusundan ilk kez oluşturduğunuz sırada bulunduğu özgün yapılandırmaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="37bf5-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="37bf5-206">İyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="37bf5-206">Optimizations</span></span>

<span data-ttu-id="37bf5-207">Şimdiye kadar derlediğiniz örnek, üst ve alt kartların her çalıştırmada aynı kalacağı *karışık*bir şekilde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="37bf5-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="37bf5-208">Tek bir değişiklik yapabiliriz: bunun yerine, tüm 52 kartlar konum değiştiren bir *karışık olarak* kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="37bf5-209">Bir karışık olarak, alt yarısı ilk kartın destedeki ilk kart haline gelmesi için destesi bir kez ayırmada kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="37bf5-210">Bu, üstteki yarısında son kartın alt kart haline geldiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="37bf5-211">Bu, tekil kod satırında basit bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="37bf5-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="37bf5-212"><xref:System.Linq.Enumerable.Take%2A> Ve<xref:System.Linq.Enumerable.Skip%2A>konumlarını değiştirerek geçerli karıştırma sorgusunu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="37bf5-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="37bf5-213">Bu, deste 'nın üst ve alt kilitlenme sırasını değiştirir:</span><span class="sxs-lookup"><span data-stu-id="37bf5-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="37bf5-214">Programı yeniden çalıştırın ve deste 'nın kendisini yeniden sıralamak için 52 yineleme aldığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="37bf5-215">Program çalışmaya devam ettiğinden bazı önemli performans düşüşlerinden de karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="37bf5-216">Bunun birçok nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-216">There are a number of reasons for this.</span></span> <span data-ttu-id="37bf5-217">Bu performans durmasının önemli nedenlerine bir tane ekleyebilirsiniz: verimsiz [*yavaş değerlendirme*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)kullanımı.</span><span class="sxs-lookup"><span data-stu-id="37bf5-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="37bf5-218">Kısaca, yavaş değerlendirme bir deyimin değerlendirmesinin değeri gerekli olana kadar gerçekleştirilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="37bf5-219">LINQ sorguları, geç değerlendirilen ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="37bf5-220">Sıralar yalnızca öğeler istendiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="37bf5-221">Genellikle bu, LINQ 'ın önemli bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="37bf5-222">Bununla birlikte, bu program gibi bir kullanımda, yürütme zamanında üstel büyümeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="37bf5-223">Bir LINQ sorgusu kullanarak özgün destesi oluşturduğumuz unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="37bf5-224">Her karıştırma, önceki destede üç LINQ sorgusu gerçekleştirerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="37bf5-225">Bunların tümü geç gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-225">All these are performed lazily.</span></span> <span data-ttu-id="37bf5-226">Bu Ayrıca, sıranın her istenilişinde yeniden gerçekleştirdikleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="37bf5-227">5 TB yinelemesine alışışınızda, ilk desteyi pek çok kez yeniden oluşturuluyor olursunuz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="37bf5-228">Bu davranışı göstermek için bir günlük yazalım.</span><span class="sxs-lookup"><span data-stu-id="37bf5-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="37bf5-229">Ardından, onu düzeltireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-229">Then, you'll fix it.</span></span>

<span data-ttu-id="37bf5-230">`Extensions.cs` Dosyanıza aşağıdaki yöntemi yazın veya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="37bf5-231">Bu genişletme yöntemi, proje dizininiz içinde adlı `debug.log` yeni bir dosya oluşturur ve o anda günlük dosyasına hangi sorgunun yürütülebileceğini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="37bf5-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="37bf5-232">Bu genişletme yöntemi sorgunun yürütüldüğünü işaretlemek için herhangi bir sorguya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="37bf5-233">Altında `File`kırmızı renkli bir çizgi görürsünüz, bunun anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="37bf5-234">Derleyici ne `File` olduğunu bilmediğinden derlenmez.</span><span class="sxs-lookup"><span data-stu-id="37bf5-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="37bf5-235">Bu sorunu çözmek için, aşağıdaki ilk satırın `Extensions.cs`altına aşağıdaki kod satırını eklediğinizden emin olun:</span><span class="sxs-lookup"><span data-stu-id="37bf5-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="37bf5-236">Bu, sorunu çözmeli ve kırmızı hata kaybolur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="37bf5-237">Ardından, her bir sorgunun tanımını bir günlük iletisiyle işaretleyin:</span><span class="sxs-lookup"><span data-stu-id="37bf5-237">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="37bf5-238">Her sorguya eriştiğinizde günlüğe kayıt yapmayın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="37bf5-239">Yalnızca özgün sorguyu oluşturduğunuzda günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-239">You log only when you create the original query.</span></span> <span data-ttu-id="37bf5-240">Programın çalıştırılması uzun sürer, ancak artık neden de görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="37bf5-241">Oturum açma özelliği etkinken karışık olarak çalışan haya 'nın dışında çalıştırırsanız, arka arkaya geri dönün.</span><span class="sxs-lookup"><span data-stu-id="37bf5-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="37bf5-242">Hala yavaş değerlendirme etkileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="37bf5-243">Tek bir çalıştırmasında, tüm değer ve cins üretimi dahil 2592 sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="37bf5-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="37bf5-244">Yaptığınız yürütmelerin sayısını azaltmak için kodun performansını buradan geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="37bf5-245">Yapabilmeniz gereken basit bir çözüm, kart destesi oluşturan orijinal LINQ sorgusunun sonuçlarını *önbelleğe* almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="37bf5-246">Şu anda sorguları yeniden yürütüyorsunuz ve do-while döngüsü bir yinelemeden sonra yeniden oluşturuyor, kartlar ve reshuffling her seferinde yeniden oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="37bf5-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="37bf5-247">Kart desteğinizi önbelleğe almak için, LINQ yöntemlerinden <xref:System.Linq.Enumerable.ToArray%2A> yararlanabilir ve <xref:System.Linq.Enumerable.ToList%2A>bunları sorgulara eklediğinizde, bunları söyledikleri eylemleri gerçekleştirir, ancak artık sonuçları hangi yönteme bağlı olarak bir dizide veya listede depolayacağız. öğesini çağırmayı tercih edersiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="37bf5-248">Her iki sorguya de <xref:System.Linq.Enumerable.ToArray%2A> LINQ metodunu ekleyin ve programı yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="37bf5-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="37bf5-249">Şimdi, karışık karıştırma 30 sorguya kadar.</span><span class="sxs-lookup"><span data-stu-id="37bf5-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="37bf5-250">Karıştırma ile birlikte yeniden çalıştırın ve benzer iyileştirmeler görürsünüz: şimdi 162 sorguları yürütür.</span><span class="sxs-lookup"><span data-stu-id="37bf5-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="37bf5-251">Lütfen bu örneğin, yavaş değerlendirmenin performans sorunlarına neden olabileceği kullanım durumlarını vurgulamak için **tasarlandığını** unutmayın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="37bf5-252">Yavaş değerlendirmenin kod performansını etkileyebileceğini görmek önemli olsa da, tüm sorguların bir şekilde çalışması gerektiğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="37bf5-253">Kullanmadan önce yaptığınız <xref:System.Linq.Enumerable.ToArray%2A> performans isabeti, kart destesi için her yeni düzenlemenin önceki düzenlemeden oluşturulanlarıdır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="37bf5-254">Yavaş değerlendirme kullanmak, her yeni deste yapılandırmasının orijinal deste tarafından oluşturulduğu, hatta oluşturan `startingDeck`kodu yürütmesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="37bf5-255">Bu, büyük miktarda ekstra iş oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="37bf5-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="37bf5-256">Uygulamada, bazı algoritmalar Eager değerlendirmesi kullanılarak iyi çalışır ve diğerleri, yavaş değerlendirme kullanarak iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="37bf5-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="37bf5-257">Günlük kullanım için, veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda, yavaş değerlendirme genellikle daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="37bf5-258">Veritabanları için, yavaş değerlendirme, daha karmaşık sorguların veritabanı işlemine yalnızca bir gidiş dönüş ve kodunuzun geri kalanına geri dönmesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="37bf5-259">Bu, yavaş veya Eager değerlendirmesi kullanmayı tercih etmeksizin, süreçlerinizi ölçmenize ve hangi tür değerlendirme türünün size en iyi performansı sunmasına bakılmaksızın LINQ esnektir.</span><span class="sxs-lookup"><span data-stu-id="37bf5-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="37bf5-260">Sonuç</span><span class="sxs-lookup"><span data-stu-id="37bf5-260">Conclusion</span></span>

<span data-ttu-id="37bf5-261">Bu projede şunları kapsamış olursunuz:</span><span class="sxs-lookup"><span data-stu-id="37bf5-261">In this project, you covered:</span></span>

- <span data-ttu-id="37bf5-262">verileri anlamlı bir sırayla toplamak için LINQ sorguları kullanma</span><span class="sxs-lookup"><span data-stu-id="37bf5-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="37bf5-263">LINQ Sorgularına kendi özel işlevselümüzü eklemek için uzantı yöntemleri yazma</span><span class="sxs-lookup"><span data-stu-id="37bf5-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="37bf5-264">LINQ sorgularımızın, düşürülmüş hız gibi performans sorunları üzerinde çalıştığı, kodumuza ait yerleri bulma</span><span class="sxs-lookup"><span data-stu-id="37bf5-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="37bf5-265">' deki geç ve Eager değerlendirmesi, LINQ sorguları ve sorgu performansı üzerinde olabilecek etkileri</span><span class="sxs-lookup"><span data-stu-id="37bf5-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="37bf5-266">LINQ 'ten itibaren, kart püf noktaları için bir teknik Magicians kullanımı hakkında biraz bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="37bf5-267">Magicians, her kartın destede nereye taşındığını denetleyebildiğinden Faro karıştırmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="37bf5-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="37bf5-268">Artık bilineceğimize göre, diğer herkese açık yapmayın!</span><span class="sxs-lookup"><span data-stu-id="37bf5-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="37bf5-269">LINQ hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="37bf5-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="37bf5-270">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="37bf5-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="37bf5-271">LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="37bf5-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="37bf5-272">Temel LINQ sorgu Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="37bf5-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [<span data-ttu-id="37bf5-273">LINQ (C#) Ile veri dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="37bf5-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [<span data-ttu-id="37bf5-274">LINQ (C#) Içinde sorgu sözdizimi ve Yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37bf5-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [<span data-ttu-id="37bf5-275">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="37bf5-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
