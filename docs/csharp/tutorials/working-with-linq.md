---
title: LINQ ile çalışma
description: Bu öğreticide LINQ ile dizileri oluşturmak, yöntemleri kullanmak için LINQ sorguları yazma ve eager ve geç değerlendirme arasında ayrım öğretir.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: b7faa75234dec62be63e96c0f15f97c6d2aa4c99
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170814"
---
# <a name="working-with-linq"></a><span data-ttu-id="45d98-103">LINQ ile çalışma</span><span class="sxs-lookup"><span data-stu-id="45d98-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="45d98-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="45d98-104">Introduction</span></span>

<span data-ttu-id="45d98-105">Bu öğretici, .NET core'da özelliklerini öğretir ve C# dili.</span><span class="sxs-lookup"><span data-stu-id="45d98-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="45d98-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="45d98-106">You’ll learn:</span></span>

*   <span data-ttu-id="45d98-107">LINQ ile dizileri oluşturma adımları.</span><span class="sxs-lookup"><span data-stu-id="45d98-107">How to generate sequences with LINQ.</span></span>
*   <span data-ttu-id="45d98-108">Nasıl kolayca kullanılabilecek yöntemleri LINQ sorguları yazma.</span><span class="sxs-lookup"><span data-stu-id="45d98-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="45d98-109">İstekli ve geç değerlendirme arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="45d98-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="45d98-110">Tüm magician temel becerilerini birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="45d98-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="45d98-111">Kısaca, faro shuffle burada yarıya birden tam olarak bir kart Destesi bölün ve ardından her yarım özgün Destesi yeniden oluşturmak için her bir karttaki shuffle karışır bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="45d98-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="45d98-112">Magicians, her kart sonra her shuffle bilinen bir konumda olan ve yinelenen bir desen sırasıdır olduğundan bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="45d98-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="45d98-113">Amaçlarınız doğrultusunda, bu veri dizisi düzenleme ışık hearted göz olur.</span><span class="sxs-lookup"><span data-stu-id="45d98-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="45d98-114">Oluşturacağınız uygulama Kart destesi oluşturmak ve ardından her zaman sırası yazma seçeneği, bir dizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="45d98-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="45d98-115">Ayrıca, özgün sırasını güncelleştirilmiş siparişe karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="45d98-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="45d98-116">Bu öğreticide, birden fazla adım vardır.</span><span class="sxs-lookup"><span data-stu-id="45d98-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="45d98-117">Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın.</span><span class="sxs-lookup"><span data-stu-id="45d98-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="45d98-118">Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/samples GitHub deposunda.</span><span class="sxs-lookup"><span data-stu-id="45d98-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="45d98-119">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="45d98-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45d98-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="45d98-120">Prerequisites</span></span>

<span data-ttu-id="45d98-121">.NET core çalıştırmak için makinenizi ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="45d98-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="45d98-122">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="45d98-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="45d98-123">Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="45d98-124">Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="45d98-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="45d98-125">Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="45d98-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="45d98-126">Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="45d98-127">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="45d98-127">Create the Application</span></span>

<span data-ttu-id="45d98-128">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="45d98-128">The first step is to create a new application.</span></span> <span data-ttu-id="45d98-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="45d98-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="45d98-130">Bu, geçerli bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="45d98-130">Make that the current directory.</span></span> <span data-ttu-id="45d98-131">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="45d98-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="45d98-132">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45d98-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="45d98-133">C# daha önce kullanmadıysanız [Bu öğreticide](console-teleprompter.md) bir C# programı yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="45d98-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="45d98-134">Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün.</span><span class="sxs-lookup"><span data-stu-id="45d98-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="45d98-135">Veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="45d98-135">Creating the Data Set</span></span>

<span data-ttu-id="45d98-136">Başlamadan önce aşağıdaki satırları başında olduğundan emin olun `Program.cs` tarafından oluşturulan dosya `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="45d98-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="45d98-137">Bu üç satır varsa (`using` deyimleri) olmayan dosyasının en üstüne programımız derlenmez.</span><span class="sxs-lookup"><span data-stu-id="45d98-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="45d98-138">Tüm ihtiyacınız olacak başvuruları sahip olduğunuza göre bir deste nelerden göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="45d98-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="45d98-139">Genellikle, bir deste oyun dört cins varsa ve her seri On üç değerleri.</span><span class="sxs-lookup"><span data-stu-id="45d98-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="45d98-140">Normalde, oluşturmayı düşünebilirsiniz bir `Card` uygulamalarımızın sağ kapalı sınıf ve koleksiyonu doldurma `Card` el ile nesneleri.</span><span class="sxs-lookup"><span data-stu-id="45d98-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="45d98-141">LINQ ile ilgilenen bir deste oluştururken, her zamanki gibi daha kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="45d98-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="45d98-142">Oluşturmak yerine bir `Card` sınıfı, paketleri ve sıralamalar, sırasıyla temsil etmek için iki dizileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-142">Instead of creating a `Card` class, you can create two sequences to represent suites and ranks, respectively.</span></span> <span data-ttu-id="45d98-143">Gerçekten basit bir çift oluşturacaksınız [ *yineleyici yöntemleri* ](../iterators.md#enumeration-sources-with-iterator-methods) cins olarak ve derecelerini oluşturacağını <xref:System.Collections.Generic.IEnumerable%601>s dize:</span><span class="sxs-lookup"><span data-stu-id="45d98-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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
<span data-ttu-id="45d98-144">Bunlar altındaki yerleştirmek `Main` yönteminde, `Program.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="45d98-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="45d98-145">Bu iki yöntem her iki yazılımınız `yield return` çalıştırılmakta olan bir dizi oluşturmak için söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="45d98-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="45d98-146">Derleyici uygulayan bir nesne oluşturur <xref:System.Collections.Generic.IEnumerable%601> ve bunların istendiği gibi dize sırası üretir.</span><span class="sxs-lookup"><span data-stu-id="45d98-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="45d98-147">Şimdi bu yineleyici yöntemlerin deste oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="45d98-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="45d98-148">LINQ sorgusu olarak ekleyeceğiniz bizim `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45d98-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="45d98-149">İncelememiz şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="45d98-149">Here's a look at it:</span></span>

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

<span data-ttu-id="45d98-150">Birden çok `from` yan tümceleri üreten bir <xref:System.Linq.Enumerable.SelectMany%2A>, ilk dizideki her öğe ikinci dizideki her öğe birleşiminden tek bir dizisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45d98-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="45d98-151">Sıralama amaçlarımız doğrultusunda büyük/küçük harf önemlidir.</span><span class="sxs-lookup"><span data-stu-id="45d98-151">The order is important for our purposes.</span></span> <span data-ttu-id="45d98-152">İlk kaynak sırası (cins) içindeki ilk öğeye (sıralamalara sahip) ikinci dizideki her öğe ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="45d98-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="45d98-153">Bu ilk uyacak tüm On üç kartları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45d98-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="45d98-154">Bu işlem, (cins) ilk dizideki her öğe tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="45d98-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="45d98-155">Bitiş değerleri tarafından izlenen cins göre sıralanmış bir deste sonucudur.</span><span class="sxs-lookup"><span data-stu-id="45d98-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="45d98-156">Bunun yerine, yukarıda kullanılan sorgu söz dizimi LINQ yazılacak seçin veya yöntemi söz dizimini kullanın, akılda tutulması gereken önemli olduğu, söz dizimi bir biçimden diğerine diğerine gitmek her zaman mümkündür.</span><span class="sxs-lookup"><span data-stu-id="45d98-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="45d98-157">Sorgu söz dizimi içinde yazılan yukarıdaki sorguda yöntem sözdizimi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="45d98-157">The above query written in query syntax can be written in method syntax as:</span></span>
```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```
<span data-ttu-id="45d98-158">Derleyici, eşdeğer yöntemi çağrısı sözdizimine sorgu sözdizimi kullanılarak yazılsa LINQ deyimleriyle çevirir.</span><span class="sxs-lookup"><span data-stu-id="45d98-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="45d98-159">Bu nedenle, söz dizimi seçiminizden bağımsız olarak sorgu iki sürümü aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="45d98-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="45d98-160">Hangi söz dizimi durumunuza en iyi şekilde çalışır seçin: zorluk yöntemi söz dizimi ile bazı üyeler sahip olduğu bir takımda çalışıyorsanız, sorgu söz dizimi kullanarak tercih ettiğiniz örneği için deneyin.</span><span class="sxs-lookup"><span data-stu-id="45d98-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="45d98-161">Devam edip bu noktada derlediğiniz örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="45d98-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="45d98-162">Tüm 52 kartları deste içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45d98-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="45d98-163">Gözlemlemek için hata ayıklayıcı altında bu örneği çalıştırmak çok yararlı bulabilirsiniz nasıl `Suits()` ve `Ranks()` bir yöntem yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="45d98-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="45d98-164">Yalnızca gerektiği gibi her bir dizideki her bir dizenin oluşturulan açıkça görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![52 kartları yazma uygulamayı gösteren konsol penceresi](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="45d98-166">Sipariş işleme</span><span class="sxs-lookup"><span data-stu-id="45d98-166">Manipulating the Order</span></span>

<span data-ttu-id="45d98-167">Ardından, nasıl kullanıp kartları Karıştırılmasına gideceğinizi odaklanın.</span><span class="sxs-lookup"><span data-stu-id="45d98-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="45d98-168">İlk adımda herhangi bir iyi shuffle Destesi iki bölme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="45d98-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="45d98-169"><xref:System.Linq.Enumerable.Take%2A> Ve <xref:System.Linq.Enumerable.Skip%2A> LINQ API'leri parçası olan yöntemler sizin için bu özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="45d98-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="45d98-170">Bunları altındaki yerleştirmek `foreach` döngü:</span><span class="sxs-lookup"><span data-stu-id="45d98-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="45d98-171">Ancak, kendi yazmak zorunda standart kitaplıkta avantajlarından yararlanmak için karışık yöntemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="45d98-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="45d98-172">Bu işlem her bir parçasının adımlarda açıklanacaktır böylece LINQ tabanlı programlar ile kullanacağınız çeşitli teknikler, oluşturduğunuz shuffle yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="45d98-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="45d98-173">Nasıl etkileşim için bazı işlevler eklemek amacıyla <xref:System.Collections.Generic.IEnumerable%601> LINQ sorguları döneceğiz, bazı özel tür adı verilen yöntemler yazmak ihtiyacınız olacak [genişletme yöntemleri](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="45d98-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="45d98-174">Kısaca, özel amaçlı bir genişletme yöntemi olduğunu *statik yöntem* ekleyen yeni işlevler için zaten varolan bir tür işlevselliği için eklemek istediğiniz özgün türünü değiştirmek zorunda kalmadan.</span><span class="sxs-lookup"><span data-stu-id="45d98-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="45d98-175">Yeni bir ekleyerek yeni bir giriş, genişletme yöntemleri sağlar *statik* programınız için sınıf dosyası adında `Extensions.cs`ve ardından ilk bulunan uzantı yöntemine oluşturmaya başlayın:</span><span class="sxs-lookup"><span data-stu-id="45d98-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span> 

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

<span data-ttu-id="45d98-176">Yöntem imzası bir süre için özel olarak parametreleri bakın:</span><span class="sxs-lookup"><span data-stu-id="45d98-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="45d98-177">Ek gördüğünüz `this` yöntemin ilk bağımsız değişkeni değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="45d98-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="45d98-178">İşlevmiş gibi bir üye yöntemi ilk bağımsız değişken türünü yöntem çağrısı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="45d98-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="45d98-179">Ayrıca bu yöntem bildiriminde girdi ve çıktı türleri nerede standart bir deyim izleyen `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="45d98-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="45d98-180">Uygulama zincirlenmesine izin LINQ yöntemleri sağlayan daha karmaşık sorgular birlikte gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="45d98-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="45d98-181">Doğal olarak, yarıları Destesi bölme olduğundan, bu yarıları birbirine birleştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="45d98-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="45d98-182">Kodda, numaralandırma aracılığıyla edinilen sıralarının her ikisi de başka bir deyişle <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> aynı anda *`interleaving`* öğeleri ve oluşturma bir sıralı:, şimdi karışık deste.</span><span class="sxs-lookup"><span data-stu-id="45d98-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="45d98-183">Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızdan gerektirir. nasıl <xref:System.Collections.Generic.IEnumerable%601> çalışır.</span><span class="sxs-lookup"><span data-stu-id="45d98-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="45d98-184"><xref:System.Collections.Generic.IEnumerable%601> Arabirimi bir yöntemi vardır: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="45d98-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="45d98-185">Tarafından döndürülen nesne <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> sonraki öğeyi ve dizideki geçerli öğe alır. bir özellik taşımak için bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="45d98-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="45d98-186">Bu iki üyeler toplamasını ve öğeleri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="45d98-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="45d98-187">Bu ayırma yöntemi, bir yineleyici yöntemini olacak bir koleksiyon oluşturma ve koleksiyon döndürmek yerine kullanacaksınız böylece `yield return` yukarıda gösterilen sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="45d98-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="45d98-188">Bu yöntemin uygulanmasını şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="45d98-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="45d98-189">Bu yöntem, yazdığınız, dönün `Main` yöntemi ve karışık bir kez Destesi:</span><span class="sxs-lookup"><span data-stu-id="45d98-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="45d98-190">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="45d98-190">Comparisons</span></span>

<span data-ttu-id="45d98-191">Kaç seçeneği Destesi ayarlamak için gereken kendi özgün siparişe yedekleme?</span><span class="sxs-lookup"><span data-stu-id="45d98-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="45d98-192">Öğrenmek için iki diziyi eşit olup olmadığını belirleyen bir yöntem yazmaktır gerekir.</span><span class="sxs-lookup"><span data-stu-id="45d98-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="45d98-193">Bu yöntem sonra seçimdeki Destesi bir döngüde arkanıza Destesi geri sırayla olduğunda kontrol edin kodu gerekir.</span><span class="sxs-lookup"><span data-stu-id="45d98-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="45d98-194">İki sıranın eşit olup olmadığını belirlemek için bir yöntem yazma basit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="45d98-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="45d98-195">Destesi karıştırmak için yazdığınız yöntemine benzer bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="45d98-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="45d98-196">Yalnızca bu zaman yerine `yield return`ing her öğe eşleşen her dizi öğelerini karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="45d98-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="45d98-197">Her bir öğe eşleşmiyorsa dizinin tamamıyla, numaralandırılmış olduğunda, dizileri aynıdır:</span><span class="sxs-lookup"><span data-stu-id="45d98-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="45d98-198">Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="45d98-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="45d98-199">Bunlar bir dizisi giriş olarak (veya bu durumda, iki sıranın) alır ve tek bir sayı değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="45d98-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="45d98-200">Terminal yöntemlerini kullanırken her zaman en son oldukları yöntemi bir LINQ yöntemleri zincirindeki sorgu, bu nedenle "terminal" adı.</span><span class="sxs-lookup"><span data-stu-id="45d98-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span> 

<span data-ttu-id="45d98-201">Destesi özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylem görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="45d98-202">Bir döngü içinde karışık kod ve sıra özgün sırayla uygulayarak olduğunda Dur `SequenceEquals()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45d98-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="45d98-203">Bir dizi yerine tek bir değer döndürdüğünden, her zaman son yöntemi herhangi bir sorgu olacaktır görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="45d98-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="45d98-204">Şu ana kadar var ve Destesi her çalmayı nasıl yeniden düzenler, Not kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="45d98-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="45d98-205">8 seçeneği sonra (yineleme do-while döngüsü), Destesi olduğu içinde ilk başlangıç LINQ Sorgu oluşturduğunuz sırada ilk yapılandırmasına döndürür.</span><span class="sxs-lookup"><span data-stu-id="45d98-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="45d98-206">En iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="45d98-206">Optimizations</span></span>

<span data-ttu-id="45d98-207">Yapılandırdığınıza kadar örnek yürüten bir *shuffle kullanıma*, burada üst ve alt kartları her çalıştırma aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="45d98-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="45d98-208">Bir değişiklik bakalım: kullanacağız bir *karışık olarak* bunun yerine, burada tüm 52 kartları değiştirmek konumu.</span><span class="sxs-lookup"><span data-stu-id="45d98-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="45d98-209">İçinde bir karışık için ilk kart böylece alt yarısında Destesi Interleave Destesi ilk kartta olur.</span><span class="sxs-lookup"><span data-stu-id="45d98-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="45d98-210">Üst kısmında son kartın altındaki kartı haline gelir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="45d98-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="45d98-211">Bu, tek satırlık bir kod için basit bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="45d98-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="45d98-212">Geçerli shuffle sorgu konumlarını geçerek güncelleştirme <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="45d98-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="45d98-213">Bu Destesi üst ve alt yarısının sırasını değiştirir:</span><span class="sxs-lookup"><span data-stu-id="45d98-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="45d98-214">Programı yeniden çalıştırın ve kendisini yeniden sıralamak Destesi için 52 yinelemeler alan görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="45d98-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="45d98-215">Bazı önemli performans performansındaki düşüşleri program çalışmaya devam ettikçe fark etmeye başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="45d98-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="45d98-216">Bunun nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="45d98-216">There are a number of reasons for this.</span></span> <span data-ttu-id="45d98-217">Bu performans bırakma başlıca nedenlerinden üstesinden: verimsiz kullanılmasına [ *geç değerlendirme*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="45d98-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="45d98-218">Kısaca, geç değerlendirme değeri gerekli olana kadar bir deyimi değerlendirmesi gerçekleştirilmez belirtir.</span><span class="sxs-lookup"><span data-stu-id="45d98-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="45d98-219">LINQ sorguları gevşek değerlendirilen ifadeleri ' dir.</span><span class="sxs-lookup"><span data-stu-id="45d98-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="45d98-220">Öğeleri yalnızca istendiğinde dizileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45d98-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="45d98-221">Genellikle, önemli bir avantajı LINQ olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="45d98-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="45d98-222">Ancak, bu programı gibi bir kullanımda bu yürütme zamanı içinde hızlı büyümesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="45d98-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="45d98-223">Biz bir LINQ Sorgu kullanarak özgün Destesi oluşturulan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="45d98-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="45d98-224">Her shuffle önceki Destesi üzerinde üç LINQ sorguları uygulayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45d98-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="45d98-225">Tüm bu gevşek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="45d98-225">All these are performed lazily.</span></span> <span data-ttu-id="45d98-226">Bu, ayrıca bunların sırası istenen olarak yeniden her zaman gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="45d98-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="45d98-227">52nd yinelemeye alma süresi, orijinal Destesi çoğu, birçok kez yeniden.</span><span class="sxs-lookup"><span data-stu-id="45d98-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="45d98-228">Bu davranış göstermek için bir günlük yazalım.</span><span class="sxs-lookup"><span data-stu-id="45d98-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="45d98-229">Ardından, bu çözeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-229">Then, you'll fix it.</span></span>

<span data-ttu-id="45d98-230">İçinde `Extensions.cs` dosya yazın ya da aşağıdaki yöntemi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="45d98-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="45d98-231">Bu genişletme yöntemi adlı yeni bir dosya oluşturur `debug.log` kayıtları ve proje dizini içinde hangi sorgu şu anda günlük dosyasına yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="45d98-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="45d98-232">Sorgu çalıştırılmış işaretlemek için herhangi bir sorgu için bir genişletme yöntemi bu eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="45d98-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="45d98-233">Ardından, her bir günlük iletisine Sorgu tanımını izleme:</span><span class="sxs-lookup"><span data-stu-id="45d98-233">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="45d98-234">Bir sorguyu her eriştiğinde oturum yok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="45d98-234">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="45d98-235">Özgün sorgu oluşturduğunuzda oturumunuzu açın.</span><span class="sxs-lookup"><span data-stu-id="45d98-235">You log only when you create the original query.</span></span> <span data-ttu-id="45d98-236">Program hala çalıştırmak uzun zaman alır, ancak artık neden görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-236">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="45d98-237">İçinde karışık açıktır, geçiş için geri dışı karışık günlüğü'yle çalıştıran sabırdan çalıştırırsanız.</span><span class="sxs-lookup"><span data-stu-id="45d98-237">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="45d98-238">Geç değerlendirme etkileri yine de görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="45d98-238">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="45d98-239">Tek bir çalıştırmada tüm değeri ve takım oluşturma dahil, 2592 sorgularını yürütür.</span><span class="sxs-lookup"><span data-stu-id="45d98-239">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="45d98-240">Yaptığınız yürütme sayısını azaltmak için kodu buraya performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="45d98-240">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="45d98-241">Yapabilirsiniz basit bir düzeltme olmaktır *önbellek* deste oluşturan özgün LINQ sorgusunun sonuçları.</span><span class="sxs-lookup"><span data-stu-id="45d98-241">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="45d98-242">Şu anda, sorguları yeniden ve her zaman do yürütüyorsunuz-döngü yinelemeyi kartları ve resshuffling deste yeniden oluşturmak, her seferinde gerçekleştirirken.</span><span class="sxs-lookup"><span data-stu-id="45d98-242">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and resshuffling it every time.</span></span> <span data-ttu-id="45d98-243">Deste önbelleğe almak için LINQ yöntemleri yararlanabilir <xref:System.Linq.Enumerable.ToArray%2A> ve <xref:System.Linq.Enumerable.ToList%2A>; sorgular ekleme, sizin bir uyarıyla bunları aynı eylemleri gerçekleştirmeniz, ancak bunlar bir dizideki veya listesi, hangi yöntemine bağlı olarak sonuçları artık depolayacağınızı çağırmak seçin.</span><span class="sxs-lookup"><span data-stu-id="45d98-243">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="45d98-244">Append LINQ yöntemi <xref:System.Linq.Enumerable.ToArray%2A> hem sorgular, hem de yeniden programını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="45d98-244">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="45d98-245">Out shuffle aşağı 30 sorguları sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="45d98-245">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="45d98-246">İçinde karışık ile yeniden çalıştırın ve benzer geliştirmeleri göreceksiniz: artık 162 sorguları yürütür.</span><span class="sxs-lookup"><span data-stu-id="45d98-246">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="45d98-247">Bu örnek olduğunu lütfen unutmayın. **tasarlanmış** geç değerlendirme neden olduğu performans zorluklarla kullanım örneklerini vurgulamaya.</span><span class="sxs-lookup"><span data-stu-id="45d98-247">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="45d98-248">Burada geç değerlendirme kod performansını etkileyebilir görmek önemli olsa da, tüm sorguları eagerly çalışması gerektiğini anlamak aynı derecede önemlidir.</span><span class="sxs-lookup"><span data-stu-id="45d98-248">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="45d98-249">Performans, isabet kullanmadan tabi <xref:System.Linq.Enumerable.ToArray%2A> önceki düzenlemeyi her yeni deste yerleşimini inşa edildiğinden olduğu.</span><span class="sxs-lookup"><span data-stu-id="45d98-249">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="45d98-250">Geç değerlendirme kullanılması anlamına gelir her yeni Destesi yapılandırma bile yerleşik kod yürütülürken özgün Destesi oluşturulan `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="45d98-250">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="45d98-251">Bu, çok miktarda ek iş neden olur.</span><span class="sxs-lookup"><span data-stu-id="45d98-251">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="45d98-252">Uygulamada, bazı algoritmalar istekli değerlendirme kullanılarak ve diğerleri de geç değerlendirme kullanarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="45d98-252">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="45d98-253">Veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda günlük kullanım için geç değerlendirme genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="45d98-253">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="45d98-254">Veritabanları için yalnızca bir gidiş dönüş için veritabanı işlemi daha sonra tekrar kodunuzun kalanını yürütmek daha karmaşık sorgular geç değerlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="45d98-254">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="45d98-255">LINQ yavaş veya istekli değerlendirme kullanır, böylece işlemlerinizi ölçün ve hangi tür değerlendirme en iyi performansı sağlar çekmek üzere seçtiğiniz esnektir.</span><span class="sxs-lookup"><span data-stu-id="45d98-255">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="45d98-256">Sonuç</span><span class="sxs-lookup"><span data-stu-id="45d98-256">Conclusion</span></span>

<span data-ttu-id="45d98-257">Bu projede kapsamına:</span><span class="sxs-lookup"><span data-stu-id="45d98-257">In this project, you covered:</span></span>
* <span data-ttu-id="45d98-258">anlamlı bir dizisi veri toplama LINQ sorguları kullanma</span><span class="sxs-lookup"><span data-stu-id="45d98-258">using LINQ queries to aggregate data into a meaningful sequence</span></span>
* <span data-ttu-id="45d98-259">LINQ sorguları için kendi özel işlevsellik eklemek için uzantı metotları yazma</span><span class="sxs-lookup"><span data-stu-id="45d98-259">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
* <span data-ttu-id="45d98-260">hız düşürülmüş alanlar burada gibi performans sorunlarını bizim LINQ sorguları karşılaşabileceğiniz bizim kod bulma</span><span class="sxs-lookup"><span data-stu-id="45d98-260">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
* <span data-ttu-id="45d98-261">LINQ sorguları ve etkileri ilgili yavaş ve istekli değerlendirme sorgu performansı üzerindeki sahip olabilir</span><span class="sxs-lookup"><span data-stu-id="45d98-261">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="45d98-262">LINQ yanı sıra, biraz teknik magicians kullanımı için kart püf noktaları hakkında bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="45d98-262">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="45d98-263">Her kart deste içinde geçtiği kontrol edebildiğiniz magicians Faro shuffle kullanın.</span><span class="sxs-lookup"><span data-stu-id="45d98-263">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="45d98-264">Artık bildiğinize göre diğer herkes için spoil yok!</span><span class="sxs-lookup"><span data-stu-id="45d98-264">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="45d98-265">LINQ hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="45d98-265">For more information on LINQ, see:</span></span>
* [<span data-ttu-id="45d98-266">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="45d98-266">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
    * [<span data-ttu-id="45d98-267">LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="45d98-267">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/introduction-to-linq.md)
    * [<span data-ttu-id="45d98-268">' De Lınq'e BaşlarkenC#</span><span class="sxs-lookup"><span data-stu-id="45d98-268">Getting Started With LINQ in C#</span></span>](../programming-guide/concepts/linq/getting-started-with-linq.md)
        - [<span data-ttu-id="45d98-269">Temel LINQ Sorgu işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="45d98-269">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
        - [<span data-ttu-id="45d98-270">LINQ ile veri dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="45d98-270">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
        - [<span data-ttu-id="45d98-271">Sorgu sözdizimi ve yöntem sözdizimi LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="45d98-271">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
        - [<span data-ttu-id="45d98-272">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="45d98-272">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
