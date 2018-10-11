---
title: LINQ ile çalışma
description: Bu öğreticide LINQ ile dizileri oluşturmak, yöntemleri kullanmak için LINQ sorguları yazma ve eager ve geç değerlendirme arasında ayrım öğretir.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: dc5f6cc4fd38b32f54a576a3947187cbed4e70e8
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086758"
---
# <a name="working-with-linq"></a><span data-ttu-id="0688f-103">LINQ ile çalışma</span><span class="sxs-lookup"><span data-stu-id="0688f-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="0688f-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="0688f-104">Introduction</span></span>

<span data-ttu-id="0688f-105">Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.</span><span class="sxs-lookup"><span data-stu-id="0688f-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="0688f-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="0688f-106">You’ll learn:</span></span>

*   <span data-ttu-id="0688f-107">LINQ ile dizileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0688f-107">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="0688f-108">Nasıl kolayca kullanılabilecek yöntemleri LINQ sorguları yazma.</span><span class="sxs-lookup"><span data-stu-id="0688f-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="0688f-109">İstekli ve geç değerlendirme arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="0688f-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="0688f-110">Tüm magician temel becerilerini birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="0688f-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="0688f-111">Kısaca, faro shuffle burada yarıya birden tam olarak bir kart Destesi bölün ve ardından her yarım özgün Destesi yeniden oluşturmak için her bir karttaki shuffle karışır bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="0688f-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="0688f-112">Magicians, her kart sonra her shuffle bilinen bir konumda olan ve yinelenen bir desen sırasıdır olduğundan bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="0688f-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="0688f-113">Amaçlarımız doğrultusunda, bu veri dizisi düzenleme ışık hearted göz olur.</span><span class="sxs-lookup"><span data-stu-id="0688f-113">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="0688f-114">Oluşturacağınız uygulama Kart destesi oluşturmak ve ardından her zaman sırası yazma seçeneği, bir dizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0688f-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="0688f-115">Ayrıca, özgün sırasını güncelleştirilmiş siparişe karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="0688f-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="0688f-116">Bu öğreticide, birden fazla adım vardır.</span><span class="sxs-lookup"><span data-stu-id="0688f-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="0688f-117">Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın.</span><span class="sxs-lookup"><span data-stu-id="0688f-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="0688f-118">Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/samples GitHub deposunda.</span><span class="sxs-lookup"><span data-stu-id="0688f-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="0688f-119">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0688f-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0688f-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0688f-120">Prerequisites</span></span>

<span data-ttu-id="0688f-121">.NET core çalıştırmak için makinenizi ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="0688f-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="0688f-122">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="0688f-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="0688f-123">Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="0688f-124">Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0688f-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="0688f-125">Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="0688f-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="0688f-126">Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="0688f-127">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="0688f-127">Create the Application</span></span>

<span data-ttu-id="0688f-128">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0688f-128">The first step is to create a new application.</span></span> <span data-ttu-id="0688f-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0688f-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="0688f-130">Bu, geçerli bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0688f-130">Make that the current directory.</span></span> <span data-ttu-id="0688f-131">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="0688f-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="0688f-132">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0688f-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="0688f-133">C# daha önce kullanmadıysanız [Bu öğreticide](console-teleprompter.md) bir C# programı yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0688f-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="0688f-134">Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün.</span><span class="sxs-lookup"><span data-stu-id="0688f-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="0688f-135">Veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0688f-135">Creating the Data Set</span></span>

<span data-ttu-id="0688f-136">Bir deste oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="0688f-136">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="0688f-137">Bu iki kaynağı (dört için uygun, on üç değerleri için bir tane) sahip bir LINQ Sorgu kullanarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="0688f-137">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="0688f-138">Bir 52 Kart destesi kaynaklarda birleştirmeniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-138">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="0688f-139">A `Console.WriteLine` deyimi içinde bir `foreach` döngü kartlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0688f-139">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="0688f-140">Sorguyu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="0688f-140">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="0688f-141">Birden çok `from` yan tümceleri üreten bir `SelectMany`, ilk dizideki her öğe ikinci dizideki her öğe birleşiminden tek bir dizisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0688f-141">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="0688f-142">Sıralama amaçlarımız doğrultusunda büyük/küçük harf önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0688f-142">The order is important for our purposes.</span></span> <span data-ttu-id="0688f-143">İlk kaynak sırası (cins) içindeki ilk öğeye (değerler) ikinci dizideki her öğe ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0688f-143">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="0688f-144">Bu ilk uyacak tüm On üç kartları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0688f-144">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="0688f-145">Bu işlem, (cins) ilk dizideki her öğe tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="0688f-145">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="0688f-146">Bitiş değerleri tarafından izlenen cins göre sıralanmış bir deste sonucudur.</span><span class="sxs-lookup"><span data-stu-id="0688f-146">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="0688f-147">Ardından, Suits() ve Ranks() yöntemler oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="0688f-147">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="0688f-148">Gerçekten basit bir dizi ile başlayalım *yineleyici yöntemleri* olarak dizeler dizisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0688f-148">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
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

<span data-ttu-id="0688f-149">Bu iki yöntem her iki yazılımınız `yield return` çalıştırılmakta olan bir dizi oluşturmak için söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="0688f-149">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="0688f-150">Derleyici uygulayan bir nesne oluşturur `IEnumerable<T>` ve bunların istendiği gibi dize sırası üretir.</span><span class="sxs-lookup"><span data-stu-id="0688f-150">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="0688f-151">Bu derleme aşağıdaki iki satırı dosyasının en üstüne eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0688f-151">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="0688f-152">Devam edip bu noktada derlediğiniz örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0688f-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="0688f-153">Tüm 52 kartları deste içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0688f-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="0688f-154">Gözlemlemek için hata ayıklayıcı altında bu örneği çalıştırmak çok yararlı bulabilirsiniz nasıl `Suits()` ve `Values()` bir yöntem yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="0688f-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="0688f-155">Yalnızca gerektiği gibi her bir dizideki her bir dizenin oluşturulan açıkça görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![52 kartları yazma uygulamayı gösteren konsol penceresi](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="0688f-157">Sipariş işleme</span><span class="sxs-lookup"><span data-stu-id="0688f-157">Manipulating the Order</span></span>

<span data-ttu-id="0688f-158">Ardından, karışık gerçekleştirebilirsiniz bir yardımcı yöntem oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="0688f-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="0688f-159">İlk adım, iki Destesi bölme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="0688f-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="0688f-160">`Take()` Ve `Skip()` LINQ API'leri parçası olan yöntemler bizim için bu özelliği sağlar:</span><span class="sxs-lookup"><span data-stu-id="0688f-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="0688f-161">Shuffle yöntemi, kendi yazmak zorunda standart kitaplıkta mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="0688f-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="0688f-162">Bu yeni yöntem LINQ tabanlı programlarla Haydi kullanacağınız çeşitli teknikler gösterir adımları yöntemi her bir parçasının açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0688f-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="0688f-163">Yöntem imzası oluşturur bir *genişletme yöntemi*:</span><span class="sxs-lookup"><span data-stu-id="0688f-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="0688f-164">Özel bir amaç için bir genişletme yöntemi olduğunu *statik yöntem.*</span><span class="sxs-lookup"><span data-stu-id="0688f-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="0688f-165">Ek gördüğünüz `this` yöntemin ilk bağımsız değişkeni değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0688f-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="0688f-166">İşlevmiş gibi bir üye yöntemi ilk bağımsız değişken türünü yöntem çağrısı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0688f-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="0688f-167">Genişletme yöntemleri, yalnızca içinde bildirilebilir `static` sınıfları, Haydi adlı yeni bir statik sınıf oluşturma `extensions` bu işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="0688f-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="0688f-168">Daha fazla genişletme yöntemleri, bu öğreticiye devam edin ve bunları aynı sınıf içinde yerleştirileceği ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="0688f-169">Ayrıca bu yöntem bildiriminde girdi ve çıktı türleri nerede standart bir deyim izleyen `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="0688f-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="0688f-170">Uygulama zincirlenmesine izin LINQ yöntemleri sağlayan daha karmaşık sorgular birlikte gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="0688f-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="0688f-171">Aynı anda hem dizileri numaralandırma, öğelerin Interleaving ve bir nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0688f-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="0688f-172">Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızdan gerektirir. nasıl `IEnumerable` çalışır.</span><span class="sxs-lookup"><span data-stu-id="0688f-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="0688f-173">`IEnumerable` Arabirimi bir yöntemi vardır: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="0688f-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="0688f-174">Tarafından döndürülen nesne `GetEnumerator()` sonraki öğeyi ve dizideki geçerli öğe alır. bir özellik taşımak için bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="0688f-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="0688f-175">Bu iki üyeler toplamasını ve öğeleri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0688f-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="0688f-176">Bu ayırma yöntemi, bir yineleyici yöntemini olacak bir koleksiyon oluşturma ve koleksiyon döndürmek yerine kullanacaksınız böylece `yield return` yukarıda gösterilen sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="0688f-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="0688f-177">Bu yöntemin uygulanmasını şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="0688f-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="0688f-178">Bu yöntem, yazdığınız, dönün `Main` yöntemi ve karışık bir kez Destesi:</span><span class="sxs-lookup"><span data-stu-id="0688f-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
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

## <a name="comparisons"></a><span data-ttu-id="0688f-179">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="0688f-179">Comparisons</span></span>

<span data-ttu-id="0688f-180">Kaç seçeneği Destesi ayarlamak için gereken kendi özgün siparişe geri görelim.</span><span class="sxs-lookup"><span data-stu-id="0688f-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="0688f-181">İki sıranın eşit olup olmadığını belirleyen bir yöntem yazmaktır gerekir.</span><span class="sxs-lookup"><span data-stu-id="0688f-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="0688f-182">Bu yöntem sonra seçimdeki Destesi bir döngüde arkanıza Destesi geri sırayla olduğunda kontrol edin kodu gerekir.</span><span class="sxs-lookup"><span data-stu-id="0688f-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="0688f-183">İki sıranın eşit olup olmadığını belirlemek için bir yöntem yazma basit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0688f-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="0688f-184">Destesi karıştırmak için yazdığınız yöntemine benzer bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="0688f-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="0688f-185">Yalnızca bu kez, her öğe iade verimi yerine, her dizinin eşleşen öğeleri karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="0688f-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="0688f-186">Her bir öğe eşleşmiyorsa dizinin tamamıyla, numaralandırılmış olduğunda, dizileri aynıdır:</span><span class="sxs-lookup"><span data-stu-id="0688f-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="0688f-187">Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0688f-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="0688f-188">Bunlar bir dizisi giriş olarak (veya bu durumda, iki sıranın) alır ve tek bir sayı değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0688f-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="0688f-189">Kullanıldığında, bu yöntemlerin her zaman son sorguda yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0688f-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="0688f-190">(Bu nedenle adı).</span><span class="sxs-lookup"><span data-stu-id="0688f-190">(Hence the name).</span></span> 

<span data-ttu-id="0688f-191">Destesi özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylem görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="0688f-192">Bir döngü içinde karışık kod ve sıra özgün sırayla uygulayarak olduğunda Dur `SequenceEquals()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0688f-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="0688f-193">Bir dizi yerine tek bir değer döndürdüğünden, her zaman son yöntemi herhangi bir sorgu olacaktır görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0688f-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="0688f-194">Örneği çalıştırmak ve nasıl 8 yinelemeden sonra orijinal yapılandırmasına için dönene kadar her çalmayı Destesi düzenlemelerinin bakın.</span><span class="sxs-lookup"><span data-stu-id="0688f-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="0688f-195">En iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="0688f-195">Optimizations</span></span>

<span data-ttu-id="0688f-196">Yapılandırdığınıza kadar örnek yürüten bir *shuffle kullanıma*, burada üst ve alt kartları her çalıştırma aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="0688f-196">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="0688f-197">Birini değiştirin ve çalıştırın olalım bir *karışık olarak*burada tüm 52 kart konumu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0688f-197">Let's make one change, and run an *in shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="0688f-198">İçinde bir karışık için ilk kart böylece alt yarısında Destesi Interleave Destesi ilk kartta olur.</span><span class="sxs-lookup"><span data-stu-id="0688f-198">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="0688f-199">Üst kısmında son kartın altındaki kartı haline gelir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0688f-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="0688f-200">Bu yalnızca bir satır farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0688f-200">That's just a one line change.</span></span> <span data-ttu-id="0688f-201">Destesi üst ve alt yarısının sırasını değiştirmek için geri çağrı güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="0688f-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="0688f-202">Programı yeniden çalıştırın ve kendisini yeniden sıralamak Destesi için 52 yinelemeler alan görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0688f-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="0688f-203">Bazı önemli performans performansındaki düşüşleri program çalışmaya devam ettikçe fark etmeye başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0688f-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="0688f-204">Bunun nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="0688f-204">There are a number of reasons for this.</span></span> <span data-ttu-id="0688f-205">Şimdi başlıca nedenlerinden üstesinden: verimsiz kullanılmasına *geç değerlendirme*.</span><span class="sxs-lookup"><span data-stu-id="0688f-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="0688f-206">LINQ sorguları gevşek değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0688f-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="0688f-207">Öğeleri yalnızca istendiğinde dizileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0688f-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="0688f-208">Genellikle, önemli bir avantajı LINQ olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0688f-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="0688f-209">Ancak, bu programı gibi bir kullanımda bu yürütme zamanı içinde hızlı büyümesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0688f-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="0688f-210">Özgün Destesi LINQ sorgusu kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="0688f-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="0688f-211">Her shuffle önceki Destesi üzerinde üç LINQ sorguları uygulayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0688f-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="0688f-212">Tüm bu gevşek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0688f-212">All these are performed lazily.</span></span> <span data-ttu-id="0688f-213">Bu, ayrıca bunların sırası istenen olarak yeniden her zaman gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0688f-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="0688f-214">52nd yinelemeye alma süresi, orijinal Destesi çoğu, birçok kez yeniden.</span><span class="sxs-lookup"><span data-stu-id="0688f-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="0688f-215">Bu davranış göstermek için bir günlük yazalım.</span><span class="sxs-lookup"><span data-stu-id="0688f-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="0688f-216">Ardından, bu çözeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-216">Then, you'll fix it.</span></span>

<span data-ttu-id="0688f-217">Sorgu çalıştırılmış işaretlemek için herhangi bir sorgu için eklenmiş bir günlük yöntemi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0688f-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="0688f-218">Ardından, her bir günlük iletisine Sorgu tanımını izleme:</span><span class="sxs-lookup"><span data-stu-id="0688f-218">Next, instrument the definition of each query with a log message:</span></span>

```csharp
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
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
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

<span data-ttu-id="0688f-219">Bir sorguyu her eriştiğinde oturum yok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0688f-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="0688f-220">Özgün sorgu oluşturduğunuzda oturumunuzu açın.</span><span class="sxs-lookup"><span data-stu-id="0688f-220">You log only when you create the original query.</span></span> <span data-ttu-id="0688f-221">Program hala çalıştırmak uzun zaman alır, ancak artık neden görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="0688f-222">Çalıştırırsanız iç çalıştıran sabırdan açık günlük kaydı ile karışık, dış shuffle için geri geçin.</span><span class="sxs-lookup"><span data-stu-id="0688f-222">If you run out of patience running the inner shuffle with logging turned on, switch back to the outer shuffle.</span></span> <span data-ttu-id="0688f-223">Geç değerlendirme etkileri yine de görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0688f-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="0688f-224">Tek bir çalıştırmada tüm değeri ve takım oluşturma dahil, 2592 sorgularını yürütür.</span><span class="sxs-lookup"><span data-stu-id="0688f-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="0688f-225">Bu yürütme önlemek için bu programı güncelleştirmek için kolay bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="0688f-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="0688f-226">LINQ yöntemleri vardır `ToArray()` ve `ToList()` , neden sorgusu çalıştırma ve sonuçları bir dizi veya bir listedeki sırasıyla depolamak.</span><span class="sxs-lookup"><span data-stu-id="0688f-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="0688f-227">Bu yöntemler yerine bir sorgu veri sonuçlarını önbelleğe kaynak sorguyu yeniden çalıştırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="0688f-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="0688f-228">Kart desteleri çağrısıyla Oluştur sorguları Ekle `ToArray()` ve sorguyu yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0688f-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="0688f-229">Tekrar çalıştırın ve dış shuffle aşağı 30 sorgudur.</span><span class="sxs-lookup"><span data-stu-id="0688f-229">Run again, and the outer shuffle is down to 30 queries.</span></span> <span data-ttu-id="0688f-230">İç karışık ile yeniden çalıştırın ve benzer geliştirmeleri göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-230">Run again with the inner shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="0688f-231">(Bunu şimdi 162 sorguları yürüten).</span><span class="sxs-lookup"><span data-stu-id="0688f-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="0688f-232">Bu örnekte, tüm sorguları eagerly çalışması gerektiğini düşünmek tarafından hatalı yorumlayan yok.</span><span class="sxs-lookup"><span data-stu-id="0688f-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="0688f-233">Bu örnek, geç değerlendirme performans zorluklarla neden olduğu durumlara vurgulamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0688f-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="0688f-234">Önceki düzenlemeyi her yeni deste yerleşimini inşa edildiğinden olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0688f-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="0688f-235">Geç değerlendirme kullanılması anlamına gelir her yeni Destesi yapılandırma bile yerleşik kod yürütülürken özgün Destesi oluşturulan `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="0688f-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="0688f-236">Bu, çok miktarda ek iş neden olur.</span><span class="sxs-lookup"><span data-stu-id="0688f-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="0688f-237">Uygulamada, bazı algoritmalar istekli değerlendirme kullanarak çok daha iyi ve diğerleri geç değerlendirme kullanarak çok daha iyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0688f-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="0688f-238">(Veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda genel olarak, geç değerlendirme çok daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="0688f-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="0688f-239">Bu gibi durumlarda, geç değerlendirme yalnızca bir gidiş dönüş için veritabanı işlemi yürütmek daha karmaşık sorgular etkinleştirir.) LINQ yavaş ve istekli değerlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="0688f-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="0688f-240">Ölçün ve en iyi seçenek seçin.</span><span class="sxs-lookup"><span data-stu-id="0688f-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="0688f-241">Yeni özellikler için hazırlama</span><span class="sxs-lookup"><span data-stu-id="0688f-241">Preparing for New Features</span></span>

<span data-ttu-id="0688f-242">Bu örnek için yazdığınız kodu işi yapan basit bir prototip oluşturmaya bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0688f-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="0688f-243">Bu bir sorun alanı keşfetmek için harika bir yoludur ve birçok özellik için kalıcı en iyi çözüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="0688f-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="0688f-244">Kullanılabilir *anonim türler* kartlar ve her bir kartı temsil için dizeler.</span><span class="sxs-lookup"><span data-stu-id="0688f-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="0688f-245">*Anonim türler* birçok üretkenlik avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="0688f-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="0688f-246">Bir sınıfı tanımlamanız gerekmez kendinize depolama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0688f-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="0688f-247">Derleyici bu tür sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0688f-247">The compiler generates the type for you.</span></span> <span data-ttu-id="0688f-248">Derleyicinin ürettiği tür birçok basit veri nesneleri için en iyi yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="0688f-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="0688f-249">Sahip *değişmez*, sonra oluşturduğu özelliklerini hiçbiri değiştirilebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0688f-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="0688f-250">Anonim türler bir derlemeye iç olduğundan bu derleme için genel API bir parçası olarak görülen değildir.</span><span class="sxs-lookup"><span data-stu-id="0688f-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="0688f-251">Anonim türler de içeren bir geçersiz kılma `ToString()` yönteminin her değeri ile biçimlendirilmiş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="0688f-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="0688f-252">Anonim türler de dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="0688f-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="0688f-253">Dönüş değerleri ya da bağımsız değişkenler bunları kullanamazsınız şekilde erişilebilir adları, sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="0688f-254">Yukarıdaki herhangi bir yöntem bu anonim türler kullanılan genel yöntemlerdir fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="0688f-255">Geçersiz kılmasını `ToString()` uygulamanın daha fazla özellik büyüdükçe istediğinizi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0688f-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="0688f-256">Örnek, dizeleri ayrıca seri ve boyut sayısı her kart için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0688f-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="0688f-257">Oldukça bitişi açan olduğu.</span><span class="sxs-lookup"><span data-stu-id="0688f-257">That's quite open ended.</span></span> <span data-ttu-id="0688f-258">C# türünde sistem yararlanarak daha iyi kod yapmak bize yardımcı olabilecek `enum` türleri için bu değerleri.</span><span class="sxs-lookup"><span data-stu-id="0688f-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="0688f-259">Cins ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="0688f-259">Start with the suits.</span></span> <span data-ttu-id="0688f-260">Bunu kullanmak için uygun bir zamandır bir `enum`:</span><span class="sxs-lookup"><span data-stu-id="0688f-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="0688f-261">`Suits()` Yöntemi ayrıca türü ve uygulama değiştirir:</span><span class="sxs-lookup"><span data-stu-id="0688f-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="0688f-262">Ardından, kartların dereceye sahip aynı değişiklik yapın:</span><span class="sxs-lookup"><span data-stu-id="0688f-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="0688f-263">Ve bunları oluşturan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="0688f-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="0688f-264">Bir son temizleme anonim bir tür üzerinde kalmak yerine, kartı temsil edecek bir tür olalım.</span><span class="sxs-lookup"><span data-stu-id="0688f-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="0688f-265">Anonim türler basit, yerel türleri için kullanışlı olsa da bu örnekte, oyun kartı kavramlarla biridir.</span><span class="sxs-lookup"><span data-stu-id="0688f-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="0688f-266">Somut bir türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0688f-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="0688f-267">Bu tür kullanan *otomatik uygulanan özellikler salt okunur* hangi Oluşturucu ayarlayın ve sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0688f-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="0688f-268">Bunu yaptığı ayrıca kullanım [dize ilişkilendirme](../language-reference/tokens/interpolated.md) biçim dizesi çıkış kolaylaştırır özelliği.</span><span class="sxs-lookup"><span data-stu-id="0688f-268">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="0688f-269">Yeni türü kullanmak için başlangıç Destesi üreten bir sorgu güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="0688f-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="0688f-270">Derleme ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0688f-270">Compile and run again.</span></span> <span data-ttu-id="0688f-271">Çıkış biraz daha net ve kod biraz daha açıktır ve daha bir kolayca genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="0688f-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="0688f-272">Sonuç</span><span class="sxs-lookup"><span data-stu-id="0688f-272">Conclusion</span></span>

<span data-ttu-id="0688f-273">Bu örnek, LINQ to kullanılan yöntemlerden bazıları gösterdi, kodu LINQ ile kolayca kullanılacak kendi yöntemlerinizi oluşturma etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="0688f-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="0688f-274">Bu ayrıca, yavaş ve istekli değerlendirmesini ve performans üzerinde karar olan etkisi arasındaki farklar gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0688f-274">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="0688f-275">Bir magician'ın teknik hakkında biraz bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="0688f-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="0688f-276">Her kart deste içinde geçtiği kontrol edebildiğiniz magicians faro shuffle kullanın.</span><span class="sxs-lookup"><span data-stu-id="0688f-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="0688f-277">Bazı ipuçlarını magician bir kart Destesi üzerine yerleştirin bir hedef kitle üyenin ve burada bu kartı gider bilerek birkaç kez seçimdeki.</span><span class="sxs-lookup"><span data-stu-id="0688f-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="0688f-278">Diğer İllüzyonları Destesi belirli bir yol ayarlamak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0688f-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="0688f-279">Bir magician ux'in gerçekleştirmeden önce Destesi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0688f-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="0688f-280">Ardından Filiz 5 kez bir dış karıştırma kullanarak Destesi karışık.</span><span class="sxs-lookup"><span data-stu-id="0688f-280">Then she will shuffle the deck 5 times using an outer shuffle.</span></span> <span data-ttu-id="0688f-281">Sahneye çıkarak, o rastgele bir deste gibi göründüğünü gösterir, 3 kez daha karışık ve tam olarak nasıl istediği ayarlamak Destesi sahip.</span><span class="sxs-lookup"><span data-stu-id="0688f-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
