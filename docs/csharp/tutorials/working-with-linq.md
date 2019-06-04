---
title: LINQ ile Çalışma
description: Bu öğreticide LINQ ile dizileri oluşturmak, yöntemleri kullanmak için LINQ sorguları yazma ve eager ve geç değerlendirme arasında ayrım öğretir.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e51fb166ccba793f9f2aa9d11a109280bf8eea93
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486990"
---
# <a name="working-with-linq"></a><span data-ttu-id="d3a2f-103">LINQ ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="d3a2f-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="d3a2f-104">Introduction</span></span>

<span data-ttu-id="d3a2f-105">Bu öğretici, .NET core'da özelliklerini öğretir ve C# dili.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="d3a2f-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-106">You’ll learn:</span></span>

- <span data-ttu-id="d3a2f-107">LINQ ile dizileri oluşturma adımları.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-107">How to generate sequences with LINQ.</span></span>
- <span data-ttu-id="d3a2f-108">Nasıl kolayca kullanılabilecek yöntemleri LINQ sorguları yazma.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-108">How to write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="d3a2f-109">İstekli ve geç değerlendirme arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="d3a2f-110">Tüm magician temel becerilerini birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="d3a2f-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="d3a2f-111">Kısaca, faro shuffle burada yarıya birden tam olarak bir kart Destesi bölün ve ardından her yarım özgün Destesi yeniden oluşturmak için her bir karttaki shuffle karışır bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="d3a2f-112">Magicians, her kart sonra her shuffle bilinen bir konumda olan ve yinelenen bir desen sırasıdır olduğundan bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="d3a2f-113">Amaçlarınız doğrultusunda, bu veri dizisi düzenleme ışık hearted göz olur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="d3a2f-114">Oluşturacağınız uygulama Kart destesi oluşturmak ve ardından her zaman sırası yazma seçeneği, bir dizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="d3a2f-115">Ayrıca, özgün sırasını güncelleştirilmiş siparişe karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="d3a2f-116">Bu öğreticide, birden fazla adım vardır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="d3a2f-117">Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="d3a2f-118">Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/samples GitHub deposunda.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="d3a2f-119">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d3a2f-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3a2f-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d3a2f-120">Prerequisites</span></span>

<span data-ttu-id="d3a2f-121">.NET core çalıştırmak için makinenizi ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="d3a2f-122">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="d3a2f-123">Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="d3a2f-124">Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="d3a2f-125">Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="d3a2f-126">Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="d3a2f-127">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-127">Create the Application</span></span>

<span data-ttu-id="d3a2f-128">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-128">The first step is to create a new application.</span></span> <span data-ttu-id="d3a2f-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="d3a2f-130">Bu, geçerli bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-130">Make that the current directory.</span></span> <span data-ttu-id="d3a2f-131">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="d3a2f-132">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="d3a2f-133">C# daha önce kullanmadıysanız [Bu öğreticide](console-teleprompter.md) bir C# programı yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="d3a2f-134">Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="creating-the-data-set"></a><span data-ttu-id="d3a2f-135">Veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-135">Creating the Data Set</span></span>

<span data-ttu-id="d3a2f-136">Başlamadan önce aşağıdaki satırları başında olduğundan emin olun `Program.cs` tarafından oluşturulan dosya `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="d3a2f-137">Bu üç satır varsa (`using` deyimleri) olmayan dosyasının en üstüne programımız derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="d3a2f-138">Tüm ihtiyacınız olacak başvuruları sahip olduğunuza göre bir deste nelerden göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="d3a2f-139">Genellikle, bir deste oyun dört cins varsa ve her seri On üç değerleri.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="d3a2f-140">Normalde, oluşturmayı düşünebilirsiniz bir `Card` uygulamalarımızın sağ kapalı sınıf ve koleksiyonu doldurma `Card` el ile nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="d3a2f-141">LINQ ile ilgilenen bir deste oluştururken, her zamanki gibi daha kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="d3a2f-142">Oluşturmak yerine bir `Card` sınıfı iki diziyi cins ve sıralamalar, sırasıyla göstermek için oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="d3a2f-143">Gerçekten basit bir çift oluşturacaksınız [ *yineleyici yöntemleri* ](../iterators.md#enumeration-sources-with-iterator-methods) cins olarak ve derecelerini oluşturacağını <xref:System.Collections.Generic.IEnumerable%601>s dize:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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

<span data-ttu-id="d3a2f-144">Bunlar altındaki yerleştirmek `Main` yönteminde, `Program.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="d3a2f-145">Bu iki yöntem her iki yazılımınız `yield return` çalıştırılmakta olan bir dizi oluşturmak için söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="d3a2f-146">Derleyici uygulayan bir nesne oluşturur <xref:System.Collections.Generic.IEnumerable%601> ve bunların istendiği gibi dize sırası üretir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="d3a2f-147">Şimdi bu yineleyici yöntemlerin deste oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="d3a2f-148">LINQ sorgusu olarak ekleyeceğiniz bizim `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="d3a2f-149">İncelememiz şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-149">Here's a look at it:</span></span>

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

<span data-ttu-id="d3a2f-150">Birden çok `from` yan tümceleri üreten bir <xref:System.Linq.Enumerable.SelectMany%2A>, ilk dizideki her öğe ikinci dizideki her öğe birleşiminden tek bir dizisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="d3a2f-151">Sıralama amaçlarımız doğrultusunda büyük/küçük harf önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-151">The order is important for our purposes.</span></span> <span data-ttu-id="d3a2f-152">İlk kaynak sırası (cins) içindeki ilk öğeye (sıralamalara sahip) ikinci dizideki her öğe ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="d3a2f-153">Bu ilk uyacak tüm On üç kartları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="d3a2f-154">Bu işlem, (cins) ilk dizideki her öğe tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="d3a2f-155">Bitiş değerleri tarafından izlenen cins göre sıralanmış bir deste sonucudur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="d3a2f-156">Bunun yerine, yukarıda kullanılan sorgu söz dizimi LINQ yazılacak seçin veya yöntemi söz dizimini kullanın, akılda tutulması gereken önemli olduğu, söz dizimi bir biçimden diğerine diğerine gitmek her zaman mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="d3a2f-157">Sorgu söz dizimi içinde yazılan yukarıdaki sorguda yöntem sözdizimi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="d3a2f-158">Derleyici, eşdeğer yöntemi çağrısı sözdizimine sorgu sözdizimi kullanılarak yazılsa LINQ deyimleriyle çevirir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="d3a2f-159">Bu nedenle, söz dizimi seçiminizden bağımsız olarak sorgu iki sürümü aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="d3a2f-160">Hangi söz dizimi durumunuza en iyi şekilde çalışır seçin: zorluk yöntemi söz dizimi ile bazı üyeler sahip olduğu bir takımda çalışıyorsanız, sorgu söz dizimi kullanarak tercih ettiğiniz örneği için deneyin.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="d3a2f-161">Devam edip bu noktada derlediğiniz örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="d3a2f-162">Tüm 52 kartları deste içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="d3a2f-163">Gözlemlemek için hata ayıklayıcı altında bu örneği çalıştırmak çok yararlı bulabilirsiniz nasıl `Suits()` ve `Ranks()` bir yöntem yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="d3a2f-164">Yalnızca gerektiği gibi her bir dizideki her bir dizenin oluşturulan açıkça görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![52 kartları yazma uygulamayı gösteren bir konsol penceresi.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="d3a2f-166">Sipariş işleme</span><span class="sxs-lookup"><span data-stu-id="d3a2f-166">Manipulating the Order</span></span>

<span data-ttu-id="d3a2f-167">Ardından, nasıl kullanıp kartları Karıştırılmasına gideceğinizi odaklanın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="d3a2f-168">İlk adımda herhangi bir iyi shuffle Destesi iki bölme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="d3a2f-169"><xref:System.Linq.Enumerable.Take%2A> Ve <xref:System.Linq.Enumerable.Skip%2A> LINQ API'leri parçası olan yöntemler sizin için bu özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="d3a2f-170">Bunları altındaki yerleştirmek `foreach` döngü:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="d3a2f-171">Ancak, kendi yazmak zorunda standart kitaplıkta avantajlarından yararlanmak için karışık yöntemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="d3a2f-172">Bu işlem her bir parçasının adımlarda açıklanacaktır böylece LINQ tabanlı programlar ile kullanacağınız çeşitli teknikler, oluşturduğunuz shuffle yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="d3a2f-173">Nasıl etkileşim için bazı işlevler eklemek amacıyla <xref:System.Collections.Generic.IEnumerable%601> LINQ sorguları döneceğiz, bazı özel tür adı verilen yöntemler yazmak ihtiyacınız olacak [genişletme yöntemleri](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d3a2f-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d3a2f-174">Kısaca, özel amaçlı bir genişletme yöntemi olduğunu *statik yöntem* ekleyen yeni işlevler için zaten varolan bir tür işlevselliği için eklemek istediğiniz özgün türünü değiştirmek zorunda kalmadan.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="d3a2f-175">Yeni bir ekleyerek yeni bir giriş, genişletme yöntemleri sağlar *statik* programınız için sınıf dosyası adında `Extensions.cs`ve ardından ilk bulunan uzantı yöntemine oluşturmaya başlayın:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

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

<span data-ttu-id="d3a2f-176">Yöntem imzası bir süre için özel olarak parametreleri bakın:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="d3a2f-177">Ek gördüğünüz `this` yöntemin ilk bağımsız değişkeni değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="d3a2f-178">İşlevmiş gibi bir üye yöntemi ilk bağımsız değişken türünü yöntem çağrısı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="d3a2f-179">Ayrıca bu yöntem bildiriminde girdi ve çıktı türleri nerede standart bir deyim izleyen `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="d3a2f-180">Uygulama zincirlenmesine izin LINQ yöntemleri sağlayan daha karmaşık sorgular birlikte gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="d3a2f-181">Doğal olarak, yarıları Destesi bölme olduğundan, bu yarıları birbirine birleştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="d3a2f-182">Kodda, numaralandırma aracılığıyla edinilen sıralarının her ikisi de başka bir deyişle <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> aynı anda *`interleaving`* öğeleri ve oluşturma bir sıralı:, şimdi karışık deste.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="d3a2f-183">Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızdan gerektirir. nasıl <xref:System.Collections.Generic.IEnumerable%601> çalışır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="d3a2f-184"><xref:System.Collections.Generic.IEnumerable%601> Arabirimi bir yöntemi vardır: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="d3a2f-185">Tarafından döndürülen nesne <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> sonraki öğeyi ve dizideki geçerli öğe alır. bir özellik taşımak için bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="d3a2f-186">Bu iki üyeler toplamasını ve öğeleri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="d3a2f-187">Bu ayırma yöntemi, bir yineleyici yöntemini olacak bir koleksiyon oluşturma ve koleksiyon döndürmek yerine kullanacaksınız böylece `yield return` yukarıda gösterilen sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="d3a2f-188">Bu yöntemin uygulanmasını şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="d3a2f-189">Bu yöntem, yazdığınız, dönün `Main` yöntemi ve karışık bir kez Destesi:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="d3a2f-190">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-190">Comparisons</span></span>

<span data-ttu-id="d3a2f-191">Kaç seçeneği Destesi ayarlamak için gereken kendi özgün siparişe yedekleme?</span><span class="sxs-lookup"><span data-stu-id="d3a2f-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="d3a2f-192">Öğrenmek için iki diziyi eşit olup olmadığını belirleyen bir yöntem yazmaktır gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="d3a2f-193">Bu yöntem sonra seçimdeki Destesi bir döngüde arkanıza Destesi geri sırayla olduğunda kontrol edin kodu gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="d3a2f-194">İki sıranın eşit olup olmadığını belirlemek için bir yöntem yazma basit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="d3a2f-195">Destesi karıştırmak için yazdığınız yöntemine benzer bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="d3a2f-196">Yalnızca bu zaman yerine `yield return`ing her öğe eşleşen her dizi öğelerini karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="d3a2f-197">Her bir öğe eşleşmiyorsa dizinin tamamıyla, numaralandırılmış olduğunda, dizileri aynıdır:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="d3a2f-198">Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="d3a2f-199">Bunlar bir dizisi giriş olarak (veya bu durumda, iki sıranın) alır ve tek bir sayı değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="d3a2f-200">Terminal yöntemlerini kullanırken her zaman en son oldukları yöntemi bir LINQ yöntemleri zincirindeki sorgu, bu nedenle "terminal" adı.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="d3a2f-201">Destesi özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylem görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="d3a2f-202">Bir döngü içinde karışık kod ve sıra özgün sırayla uygulayarak olduğunda Dur `SequenceEquals()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="d3a2f-203">Bir dizi yerine tek bir değer döndürdüğünden, her zaman son yöntemi herhangi bir sorgu olacaktır görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="d3a2f-204">Şu ana kadar var ve Destesi her çalmayı nasıl yeniden düzenler, Not kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="d3a2f-205">8 seçeneği sonra (yineleme do-while döngüsü), Destesi olduğu içinde ilk başlangıç LINQ Sorgu oluşturduğunuz sırada ilk yapılandırmasına döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="d3a2f-206">En iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="d3a2f-206">Optimizations</span></span>

<span data-ttu-id="d3a2f-207">Yapılandırdığınıza kadar örnek yürüten bir *shuffle kullanıma*, burada üst ve alt kartları her çalıştırma aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="d3a2f-208">Bir değişiklik bakalım: kullanacağız bir *karışık olarak* bunun yerine, burada tüm 52 kartları değiştirmek konumu.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="d3a2f-209">İçinde bir karışık için ilk kart böylece alt yarısında Destesi Interleave Destesi ilk kartta olur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="d3a2f-210">Üst kısmında son kartın altındaki kartı haline gelir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="d3a2f-211">Bu, tek satırlık bir kod için basit bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="d3a2f-212">Geçerli shuffle sorgu konumlarını geçerek güncelleştirme <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="d3a2f-213">Bu Destesi üst ve alt yarısının sırasını değiştirir:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="d3a2f-214">Programı yeniden çalıştırın ve kendisini yeniden sıralamak Destesi için 52 yinelemeler alan görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="d3a2f-215">Bazı önemli performans performansındaki düşüşleri program çalışmaya devam ettikçe fark etmeye başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="d3a2f-216">Bunun nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-216">There are a number of reasons for this.</span></span> <span data-ttu-id="d3a2f-217">Bu performans bırakma başlıca nedenlerinden üstesinden: verimsiz kullanılmasına [ *geç değerlendirme*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d3a2f-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="d3a2f-218">Kısaca, geç değerlendirme değeri gerekli olana kadar bir deyimi değerlendirmesi gerçekleştirilmez belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="d3a2f-219">LINQ sorguları gevşek değerlendirilen ifadeleri ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="d3a2f-220">Öğeleri yalnızca istendiğinde dizileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="d3a2f-221">Genellikle, önemli bir avantajı LINQ olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="d3a2f-222">Ancak, bu programı gibi bir kullanımda bu yürütme zamanı içinde hızlı büyümesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="d3a2f-223">Biz bir LINQ Sorgu kullanarak özgün Destesi oluşturulan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="d3a2f-224">Her shuffle önceki Destesi üzerinde üç LINQ sorguları uygulayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="d3a2f-225">Tüm bu gevşek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-225">All these are performed lazily.</span></span> <span data-ttu-id="d3a2f-226">Bu, ayrıca bunların sırası istenen olarak yeniden her zaman gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="d3a2f-227">52nd yinelemeye alma süresi, orijinal Destesi çoğu, birçok kez yeniden.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="d3a2f-228">Bu davranış göstermek için bir günlük yazalım.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="d3a2f-229">Ardından, bu çözeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-229">Then, you'll fix it.</span></span>

<span data-ttu-id="d3a2f-230">İçinde `Extensions.cs` dosya yazın ya da aşağıdaki yöntemi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="d3a2f-231">Bu genişletme yöntemi adlı yeni bir dosya oluşturur `debug.log` kayıtları ve proje dizini içinde hangi sorgu şu anda günlük dosyasına yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="d3a2f-232">Sorgu çalıştırılmış işaretlemek için herhangi bir sorgu için bir genişletme yöntemi bu eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="d3a2f-233">Ardından, her bir günlük iletisine Sorgu tanımını izleme:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-233">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="d3a2f-234">Bir sorguyu her eriştiğinde oturum yok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-234">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="d3a2f-235">Özgün sorgu oluşturduğunuzda oturumunuzu açın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-235">You log only when you create the original query.</span></span> <span data-ttu-id="d3a2f-236">Program hala çalıştırmak uzun zaman alır, ancak artık neden görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-236">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="d3a2f-237">İçinde karışık açıktır, geçiş için geri dışı karışık günlüğü'yle çalıştıran sabırdan çalıştırırsanız.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-237">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="d3a2f-238">Geç değerlendirme etkileri yine de görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-238">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="d3a2f-239">Tek bir çalıştırmada tüm değeri ve takım oluşturma dahil, 2592 sorgularını yürütür.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-239">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="d3a2f-240">Yaptığınız yürütme sayısını azaltmak için kodu buraya performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-240">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="d3a2f-241">Yapabilirsiniz basit bir düzeltme olmaktır *önbellek* deste oluşturan özgün LINQ sorgusunun sonuçları.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-241">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="d3a2f-242">Şu anda, sorguları yeniden ve her zaman do yürütüyorsunuz-döngü yineleme gerçekleştirirken deste yeniden oluşturmak ve her seferinde reshuffling.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-242">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="d3a2f-243">Deste önbelleğe almak için LINQ yöntemleri yararlanabilir <xref:System.Linq.Enumerable.ToArray%2A> ve <xref:System.Linq.Enumerable.ToList%2A>; sorgular ekleme, sizin bir uyarıyla bunları aynı eylemleri gerçekleştirmeniz, ancak bunlar bir dizideki veya listesi, hangi yöntemine bağlı olarak sonuçları artık depolayacağınızı çağırmak seçin.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-243">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="d3a2f-244">Append LINQ yöntemi <xref:System.Linq.Enumerable.ToArray%2A> hem sorgular, hem de yeniden programını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-244">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="d3a2f-245">Out shuffle aşağı 30 sorguları sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-245">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="d3a2f-246">İçinde karışık ile yeniden çalıştırın ve benzer geliştirmeleri göreceksiniz: artık 162 sorguları yürütür.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-246">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="d3a2f-247">Bu örnek olduğunu lütfen unutmayın. **tasarlanmış** geç değerlendirme neden olduğu performans zorluklarla kullanım örneklerini vurgulamaya.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-247">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="d3a2f-248">Burada geç değerlendirme kod performansını etkileyebilir görmek önemli olsa da, tüm sorguları eagerly çalışması gerektiğini anlamak aynı derecede önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-248">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="d3a2f-249">Performans, isabet kullanmadan tabi <xref:System.Linq.Enumerable.ToArray%2A> önceki düzenlemeyi her yeni deste yerleşimini inşa edildiğinden olduğu.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-249">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="d3a2f-250">Geç değerlendirme kullanılması anlamına gelir her yeni Destesi yapılandırma bile yerleşik kod yürütülürken özgün Destesi oluşturulan `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-250">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="d3a2f-251">Bu, çok miktarda ek iş neden olur.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-251">That causes a large amount of extra work.</span></span>

<span data-ttu-id="d3a2f-252">Uygulamada, bazı algoritmalar istekli değerlendirme kullanılarak ve diğerleri de geç değerlendirme kullanarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-252">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="d3a2f-253">Veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda günlük kullanım için geç değerlendirme genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-253">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="d3a2f-254">Veritabanları için yalnızca bir gidiş dönüş için veritabanı işlemi daha sonra tekrar kodunuzun kalanını yürütmek daha karmaşık sorgular geç değerlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-254">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="d3a2f-255">LINQ yavaş veya istekli değerlendirme kullanır, böylece işlemlerinizi ölçün ve hangi tür değerlendirme en iyi performansı sağlar çekmek üzere seçtiğiniz esnektir.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-255">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="d3a2f-256">Sonuç</span><span class="sxs-lookup"><span data-stu-id="d3a2f-256">Conclusion</span></span>

<span data-ttu-id="d3a2f-257">Bu projede kapsamına:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-257">In this project, you covered:</span></span>
- <span data-ttu-id="d3a2f-258">anlamlı bir dizisi veri toplama LINQ sorguları kullanma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-258">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="d3a2f-259">LINQ sorguları için kendi özel işlevsellik eklemek için uzantı metotları yazma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-259">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="d3a2f-260">hız düşürülmüş alanlar burada gibi performans sorunlarını bizim LINQ sorguları karşılaşabileceğiniz bizim kod bulma</span><span class="sxs-lookup"><span data-stu-id="d3a2f-260">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="d3a2f-261">LINQ sorguları ve etkileri ilgili yavaş ve istekli değerlendirme sorgu performansı üzerindeki sahip olabilir</span><span class="sxs-lookup"><span data-stu-id="d3a2f-261">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="d3a2f-262">LINQ yanı sıra, biraz teknik magicians kullanımı için kart püf noktaları hakkında bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-262">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="d3a2f-263">Her kart deste içinde geçtiği kontrol edebildiğiniz magicians Faro shuffle kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3a2f-263">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="d3a2f-264">Artık bildiğinize göre diğer herkes için spoil yok!</span><span class="sxs-lookup"><span data-stu-id="d3a2f-264">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="d3a2f-265">LINQ hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="d3a2f-265">For more information on LINQ, see:</span></span>
- [<span data-ttu-id="d3a2f-266">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d3a2f-266">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="d3a2f-267">LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="d3a2f-267">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="d3a2f-268">Temel LINQ Sorgu işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d3a2f-268">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [<span data-ttu-id="d3a2f-269">LINQ ile veri dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="d3a2f-269">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [<span data-ttu-id="d3a2f-270">Sorgu sözdizimi ve yöntem sözdizimi LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d3a2f-270">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [<span data-ttu-id="d3a2f-271">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d3a2f-271">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
    