---
title: "LINQ ile çalışma"
description: "Bu öğretici LINQ sıralarıyla oluşturmak, kullanım için yöntemleri LINQ sorguları yazma ve istekli ve geç değerlendirme arasında ayrım öğretir."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e9707d3b67a80fface2c26c589780c60c2e293f7
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="1adf2-104">LINQ ile çalışma</span><span class="sxs-lookup"><span data-stu-id="1adf2-104">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="1adf2-105">Giriş</span><span class="sxs-lookup"><span data-stu-id="1adf2-105">Introduction</span></span>

<span data-ttu-id="1adf2-106">Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1adf2-107">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1adf2-107">You’ll learn:</span></span>

*   <span data-ttu-id="1adf2-108">LINQ ile sıraları oluşturma</span><span class="sxs-lookup"><span data-stu-id="1adf2-108">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="1adf2-109">Kolayca kullanılabilir yöntemleri LINQ sorguları yazma yapma.</span><span class="sxs-lookup"><span data-stu-id="1adf2-109">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="1adf2-110">İstekli ve geç değerlendirme arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="1adf2-110">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="1adf2-111">Tüm magician temel becerileri birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro karışık](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="1adf2-111">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="1adf2-112">Kısaca, faro karışık burada yarısı içinde tam olarak bir kart deste bölme ve ardından her bir özgün deste yeniden oluşturmak için her yarım kartından karışık interleaves bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-112">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="1adf2-113">Magicians her karttır sonra her karışık bilinen bir konumda ve yinelenen bir desen sırasını olduğu için bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-113">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="1adf2-114">Bizim, bu veri dizisi düzenleme bir ışık hearted göz amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-114">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="1adf2-115">Oluşturacağınız uygulama kartı deste oluşturun ve sonra her zaman sırası yazma seçeneği, bir dizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1adf2-115">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="1adf2-116">Ayrıca orijinal siparişine güncelleştirilmiş sipariş karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-116">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="1adf2-117">Bu öğretici, birden çok adım vardır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-117">This tutorial has multiple steps.</span></span> <span data-ttu-id="1adf2-118">Her adımdan sonra uygulamayı çalıştırın ve ilerleme bakın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-118">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="1adf2-119">Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) dotnet/belgeler GitHub deposunda.</span><span class="sxs-lookup"><span data-stu-id="1adf2-119">You can also see the [completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) in the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="1adf2-120">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1adf2-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1adf2-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1adf2-121">Prerequisites</span></span>

<span data-ttu-id="1adf2-122">.NET core çalışmasına, makine Kurulum gerekir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-122">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="1adf2-123">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="1adf2-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="1adf2-124">Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-124">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="1adf2-125">Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="1adf2-126">Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu.</span><span class="sxs-lookup"><span data-stu-id="1adf2-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="1adf2-127">Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-127">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1adf2-128">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="1adf2-128">Create the Application</span></span>

<span data-ttu-id="1adf2-129">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-129">The first step is to create a new application.</span></span> <span data-ttu-id="1adf2-130">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1adf2-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1adf2-131">Geçerli dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1adf2-131">Make that the current directory.</span></span> <span data-ttu-id="1adf2-132">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="1adf2-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1adf2-133">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="1adf2-134">Hiç C# daha önce kullanmadıysanız [Bu öğretici](console-teleprompter.md) C# programının yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1adf2-134">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="1adf2-135">Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün.</span><span class="sxs-lookup"><span data-stu-id="1adf2-135">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="1adf2-136">Veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1adf2-136">Creating the Data Set</span></span>

<span data-ttu-id="1adf2-137">Bir deste oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1adf2-137">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="1adf2-138">Bu iki kaynaklarına (dört için uygun, on üç değerleri için bir tane) sahip bir LINQ Sorgu kullanarak gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-138">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="1adf2-139">Bu kaynakları 52 kart deste birleştirmeniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-139">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="1adf2-140">A `Console.WriteLine` deyimi içinde bir `foreach` döngü kartları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1adf2-140">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="1adf2-141">Sorgu şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1adf2-141">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="1adf2-142">Birden çok `from` yan tümceleri üreten bir `SelectMany`, ilk dizisindeki her öğe ikinci dizideki her öğe ile birleştirerek tek bir dizi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-142">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="1adf2-143">Bizim amaçlar için sıralama önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-143">The order is important for our purposes.</span></span> <span data-ttu-id="1adf2-144">İlk kaynak dizisi (Setleri) ilk öğe (değerler) ikinci dizisindeki her öğe ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-144">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="1adf2-145">Bu ilk seri tüm On üç kartı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-145">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="1adf2-146">Bu işlem, ilk sırada (Setleri) her bir öğesiyle yinelenir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-146">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="1adf2-147">Sonuç değerleri tarafından izlenen Setleri göre sıralanmış deste ' dir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-147">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="1adf2-148">Ardından, Suits() ve Ranks() yöntemleri yapı gerekir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-148">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="1adf2-149">Çok basit bir dizi birlikte başlayalım *yineleyici metotları* olarak dizeler dizisi oluştur:</span><span class="sxs-lookup"><span data-stu-id="1adf2-149">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

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

<span data-ttu-id="1adf2-150">Bu iki yöntem hem kullanan `yield return` çalıştıkları gibi bir dizi üretmek için sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="1adf2-150">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="1adf2-151">Arabirimini uygulayan bir nesneye derleyici derlemeler `IEnumerable<T>` ve bunların istendiği gibi bir dizi dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-151">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="1adf2-152">Devam etmek ve bu noktada oluşturuncaya örneğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="1adf2-153">Bunu tüm 52 kartları deste görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1adf2-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="1adf2-154">Bu örnek izlemek için bir hata ayıklayıcı altında çalıştırmak çok faydalı bulabileceğiniz nasıl `Suits()` ve `Values()` bir yöntem yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="1adf2-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="1adf2-155">Yalnızca gerektiği gibi her dizisindeki her dize oluşturulur açıkça görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Out 52 kart yazma uygulamasını gösteren konsol penceresi](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="1adf2-157">Sıra düzenleme</span><span class="sxs-lookup"><span data-stu-id="1adf2-157">Manipulating the Order</span></span>

<span data-ttu-id="1adf2-158">Ardından, şimdi karışık gerçekleştirebileceğiniz bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1adf2-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="1adf2-159">İlk iki deste bölüneceği bir adımdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="1adf2-160">`Take()` Ve `Skip()` LINQ API'leri parçası olan yöntemleri bize bu özelliği sağlar:</span><span class="sxs-lookup"><span data-stu-id="1adf2-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="1adf2-161">Kendi yazma gerekir böylece karışık yöntemi Standart kitaplığında yok.</span><span class="sxs-lookup"><span data-stu-id="1adf2-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="1adf2-162">Bu yeni yöntemi LINQ tabanlı programlarla sağlandığından kullanacağınız çeşitli teknikler gösterilmektedir adımları yönteminde her bölümünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="1adf2-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="1adf2-163">Yöntem için imza oluşturur bir *genişletme yöntemi*:</span><span class="sxs-lookup"><span data-stu-id="1adf2-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="1adf2-164">Özel bir amaç için bir genişletme yöntemi olan *statik yöntemi.*</span><span class="sxs-lookup"><span data-stu-id="1adf2-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="1adf2-165">Eklenmesi görebilirsiniz `this` yöntemi ilk bağımsız değişken değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1adf2-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="1adf2-166">Dizinindeymiş gibi ilk bağımsız değişkenin türünün üye yöntemi yöntemi çağırma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="1adf2-167">Genişletme yöntemleri, yalnızca içinde bildirilebilir `static` sağlandığından sınıfları adlı yeni bir statik sınıf oluşturmak `extensions` bu işlevsellik için.</span><span class="sxs-lookup"><span data-stu-id="1adf2-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="1adf2-168">Bu öğretici devam etmek ve bu aynı sınıfta yerleştirilecek gibi daha fazla genişletme yöntemleri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="1adf2-169">Ayrıca bu yöntem bildirimi giriş ve çıkış türleri nerede standart bir deyim izleyen `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="1adf2-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="1adf2-170">Uygulama zincirlenmesine izin LINQ yöntemleri sağlar birlikte daha karmaşık sorgular gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1adf2-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

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

<span data-ttu-id="1adf2-171">Aynı anda hem sıraları numaralandırma, öğelerin Interleaving ve bir nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1adf2-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="1adf2-172">Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızı gerektirir nasıl `IEnumerable` çalışır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="1adf2-173">`IEnumerable` Arabirimi bir yöntem vardır: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="1adf2-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="1adf2-174">Tarafından döndürülen nesne `GetEnumerator()` sonraki öğeye ve dizisi geçerli öğe alır bir özellik taşımak için bir yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="1adf2-175">Bu iki üyeler toplamasını ve öğeleri dönmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="1adf2-176">Bu ayırma yöntemi bir yineleyici yöntemi olacak bir koleksiyon oluşturma ve koleksiyonu döndüren yerine kullanacağınız şekilde `yield return` yukarıda gösterilen sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="1adf2-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="1adf2-177">Bu yöntemin kullanımı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1adf2-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="1adf2-178">Bu yöntem yazdıktan, geri dönüp `Main` yöntemi ve karışık bir kez deste:</span><span class="sxs-lookup"><span data-stu-id="1adf2-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="1adf2-179">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="1adf2-179">Comparisons</span></span>

<span data-ttu-id="1adf2-180">Kaç tane seçeneği deste ayarlamak için gereken özgün siparişe geri görelim.</span><span class="sxs-lookup"><span data-stu-id="1adf2-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="1adf2-181">İki sıraları eşit olup olmadığını belirleyen bir yöntem yazmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="1adf2-182">Bu yöntem aldıktan sonra döngü ve deste geri sırayla olduğunda denetleyin deste seçimdeki kod yerleştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="1adf2-183">İki sıraları eşit olup olmadığını belirlemek için bir yöntem yazma kolay olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="1adf2-184">Deste karışık yazdığınız yöntemine benzer bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="1adf2-185">Yalnızca bu kez, her öğeye döndürme verim yerine, her dizinin eşleşen öğeleri karşılaştırmak.</span><span class="sxs-lookup"><span data-stu-id="1adf2-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="1adf2-186">Her bir öğe eşleşmiyorsa tüm sırası, numaralandırılmış olduğunda, dizileri aynıdır:</span><span class="sxs-lookup"><span data-stu-id="1adf2-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="1adf2-187">Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="1adf2-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="1adf2-188">Bunlar bir dizi girişi olarak (veya bu durumda, iki sıraları) alın ve tek bir sayı değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1adf2-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="1adf2-189">Kullanıldığında, bu yöntemlerin her zaman son bir sorgunun bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="1adf2-190">(Bu nedenle adı).</span><span class="sxs-lookup"><span data-stu-id="1adf2-190">(Hence the name).</span></span> 

<span data-ttu-id="1adf2-191">Deste özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylemde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="1adf2-192">Karışık kod döngü içinde koy ve dizisi özgün sırayla uygulayarak olduğunda Durdur `SequenceEquals()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1adf2-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="1adf2-193">Bir dizi yerine tek bir değer döndürdüğünden, her zaman herhangi bir sorgu son yönteminde olacaktır görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1adf2-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="1adf2-194">Örneği çalıştırmak ve 8 yinelemeden sonra orijinal yapılandırmasına döndürür kadar nasıl deste her çalmayı yeniden düzenler bakın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="1adf2-195">En iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="1adf2-195">Optimizations</span></span>

<span data-ttu-id="1adf2-196">Oluşturulan kadarki örnek yürüten bir *karışık olarak*, burada üst ve alt kartları her çalıştırmada aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-196">The sample you've built so far executes an *in shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="1adf2-197">Bir değiştirin ve çalıştırın olalım bir *karışık çıkışı*, burada tüm 52 kartları konumunu değiştirme.</span><span class="sxs-lookup"><span data-stu-id="1adf2-197">Let's make one change, and run an *out shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="1adf2-198">Bir çıkış karışık için ilk kartı böylece alt yarısında deste Interleave deste ilk kart olur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-198">For an out shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="1adf2-199">Üst yarısındaki son kartı altındaki kartı hale anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="1adf2-200">Yalnızca tek bir çizgi değişiklik olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-200">That's just a one line change.</span></span> <span data-ttu-id="1adf2-201">Deste üst ve alt yarısının sırasını değiştirmek için karışık çağrısı güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="1adf2-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="1adf2-202">Programı yeniden çalıştırın ve kendisini yeniden sıralamak deste 52 yinelemeleri sürdüğünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="1adf2-203">Program çalıştırmaya devam gibi bazı önemli performans degradations fark edilecek başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="1adf2-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="1adf2-204">Bunun nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-204">There are a number of reasons for this.</span></span> <span data-ttu-id="1adf2-205">Şimdi başlıca nedenlerinden üstesinden gelmek: verimsiz kullanımı *geç değerlendirme*.</span><span class="sxs-lookup"><span data-stu-id="1adf2-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="1adf2-206">LINQ sorgularını gevşek değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="1adf2-207">Öğeleri yalnızca istendiği gibi dizileri üretilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="1adf2-208">Genellikle, önemli bir avantajı LINQ olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="1adf2-209">Ancak, bu programı gibi bir kullanımda bu yürütme süresini üstel artışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="1adf2-210">Özgün deste LINQ sorgusu kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1adf2-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="1adf2-211">Her karışık önceki deste üzerinde üç LINQ sorgularını gerçekleştirerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="1adf2-212">Bunların tümü gevşek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-212">All these are performed lazily.</span></span> <span data-ttu-id="1adf2-213">Ayrıca istenen sırası her zaman tekrar gerçekleştirilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="1adf2-214">52nd yinelemeye alma zamanına göre özgün deste çoğu, birçok kez yeniden.</span><span class="sxs-lookup"><span data-stu-id="1adf2-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="1adf2-215">Bu davranış göstermek için bir günlük yazalım.</span><span class="sxs-lookup"><span data-stu-id="1adf2-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="1adf2-216">Ardından, onu düzeltmesi.</span><span class="sxs-lookup"><span data-stu-id="1adf2-216">Then, you'll fix it.</span></span>

<span data-ttu-id="1adf2-217">Sorgu yürütülür işaretlemek için herhangi bir sorgu için eklenen bir günlük yöntemi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="1adf2-218">Ardından, her bir günlük iletisine sorguyla tanımını izleme:</span><span class="sxs-lookup"><span data-stu-id="1adf2-218">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="1adf2-219">Bir sorgu her eriştiğinde oturum yok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1adf2-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="1adf2-220">Yalnızca özgün sorgu oluşturduğunuzda, oturum açın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-220">You log only when you create the original query.</span></span> <span data-ttu-id="1adf2-221">Program hala çalıştırmak için uzun bir zaman alır, ancak artık neden görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="1adf2-222">Çalıştırırsanız açık günlük ile dış çalıştıran sabırdan karışık, geri iç karışık için geçin.</span><span class="sxs-lookup"><span data-stu-id="1adf2-222">If you run out of patience running the outer shuffle with logging turned on, switch back to the inner shuffle.</span></span> <span data-ttu-id="1adf2-223">Geç değerlendirme etkileri hala görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="1adf2-224">Tek çalıştırmada tüm değer ve seri oluşturma gibi 2592 sorguları yürütür.</span><span class="sxs-lookup"><span data-stu-id="1adf2-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="1adf2-225">Bu yürütmeleri önlemek için bu programı güncelleştirmek için kolay bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="1adf2-226">LINQ yöntemlerdir `ToArray()` ve `ToList()` , sorguyu çalıştırmak neden ve sonuçları bir dizi veya bir liste, sırasıyla depolamak.</span><span class="sxs-lookup"><span data-stu-id="1adf2-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="1adf2-227">Bu yöntemler bir sorgu veri sonuçlarını önbelleğe yerine kaynak sorguyu yeniden çalıştırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="1adf2-228">Ekleme çağrısıyla kartı deste oluşturmak sorgularını `ToArray()` ve sorguyu yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1adf2-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="1adf2-229">Yeniden çalıştırın ve iç karışık aşağıya doğru 30 sorgudur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-229">Run again, and the inner shuffle is down to 30 queries.</span></span> <span data-ttu-id="1adf2-230">Dış karışık ile yeniden çalıştırın ve benzer geliştirmeleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-230">Run again with the outer shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="1adf2-231">(Bunu şimdi 162 sorguları yürüten).</span><span class="sxs-lookup"><span data-stu-id="1adf2-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="1adf2-232">Bu örnekte, tüm sorguları isteğini önleyebiliriz çalışması gerektiğini göz önünde tarafından hatalı yorumlayan yok.</span><span class="sxs-lookup"><span data-stu-id="1adf2-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="1adf2-233">Bu örnek, geç değerlendirme performans sorunlar neden olduğu kullanım örnekleri vurgulamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="1adf2-234">Her yeni deste düzenlenmesi önceki düzenlemeden diğerine oluşturulduğundan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="1adf2-235">Geç değerlendirme kullanılması anlamına gelir her yeni deste yapılandırma bile yerleşik kod yürütmek özgün deste yerleşik `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="1adf2-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="1adf2-236">Bu, büyük miktarda ek iş neden olur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="1adf2-237">Uygulamada, bazı algoritmaları istekli değerlendirme kullanarak daha iyi ve diğerleri geç değerlendirme kullanarak daha iyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="1adf2-238">(Veri kaynağı bir veritabanı motoru gibi ayrı bir işlem olduğunda genel olarak, geç değerlendirme kadar daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="1adf2-239">Bu durumlarda, geç değerlendirme veritabanı işlemi için yalnızca bir gidiş dönüş yürütmek daha karmaşık sorgular etkinleştirir.) LINQ yavaş ve istekli değerlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="1adf2-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="1adf2-240">Ölçü ve en iyi seçenek seçin.</span><span class="sxs-lookup"><span data-stu-id="1adf2-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="1adf2-241">Yeni özellikler için hazırlama</span><span class="sxs-lookup"><span data-stu-id="1adf2-241">Preparing for New Features</span></span>

<span data-ttu-id="1adf2-242">Bu örnek için yazdığınız kodu işi halleder basit bir prototip oluşturma örneğidir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="1adf2-243">Bu bir sorun alanı keşfetmek için harika bir yoludur ve birçok özellik için en iyi kalıcı çözüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="1adf2-244">İşlevden *anonim türler* kartları ve her kartı temsil edildiği için dizeler.</span><span class="sxs-lookup"><span data-stu-id="1adf2-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="1adf2-245">*Anonim türler* birçok üretkenlik avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="1adf2-246">Bir sınıf tanımlama gerekmez kendinize depolama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1adf2-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="1adf2-247">Derleyici türü sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1adf2-247">The compiler generates the type for you.</span></span> <span data-ttu-id="1adf2-248">Oluşturulan derleyici türü çok basit veri nesneler için en iyi uygulamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="1adf2-249">Bunun *değişmez*, onu oluşturulan sonra özelliklerini hiçbiri değiştirilebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="1adf2-250">Anonim türler bir derlemeye iç olduğundan bu derleme için genel API'si bir parçası olarak görülen değil.</span><span class="sxs-lookup"><span data-stu-id="1adf2-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="1adf2-251">Anonim türler de içeren bir geçersiz kılma `ToString()` yöntemi her değeri ile biçimlendirilmiş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="1adf2-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="1adf2-252">Anonim türler de dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="1adf2-253">Dönüş değerleri veya bağımsız olarak bunları kullanamazsınız şekilde erişilebilir adları sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="1adf2-254">Yukarıdaki herhangi bir yöntem bu anonim türler kullanılan genel yöntemlerdir fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="1adf2-255">Geçersiz kılma `ToString()` uygulamanın daha fazla özellik büyüdükçe istediğinizi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="1adf2-256">Örnek dizeleri her kart derecesini ve uyacak için de kullanır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="1adf2-257">Oldukça sona erdi açan değil.</span><span class="sxs-lookup"><span data-stu-id="1adf2-257">That's quite open ended.</span></span> <span data-ttu-id="1adf2-258">C# tür sistemi yararlanarak daha iyi bir kod olun yardımcı olabilecek `enum` türleri için bu değerleri.</span><span class="sxs-lookup"><span data-stu-id="1adf2-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="1adf2-259">Setleri ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-259">Start with the suits.</span></span> <span data-ttu-id="1adf2-260">Bu kullanmak için uygun bir zamandır bir `enum`:</span><span class="sxs-lookup"><span data-stu-id="1adf2-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="1adf2-261">`Suits()` Yöntemi de değişiklikleri türü ve uygulama:</span><span class="sxs-lookup"><span data-stu-id="1adf2-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="1adf2-262">Ardından, kartları dereceye sahip aynı değişiklik yapın:</span><span class="sxs-lookup"><span data-stu-id="1adf2-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="1adf2-263">Ve bunları oluşturan yöntem:</span><span class="sxs-lookup"><span data-stu-id="1adf2-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="1adf2-264">Bir son temizleme anonim bir tür kalmak yerine, kartı temsil etmek için bir tür olalım.</span><span class="sxs-lookup"><span data-stu-id="1adf2-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="1adf2-265">Anonim türler basit, yerel türleri için harika, ancak bu örnekte, oyun kartı kavramlarla biridir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="1adf2-266">Somut bir türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf2-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="1adf2-267">Bu tür kullanır *otomatik uygulanan salt okunur özellikler* oluşturucuda ayarlayın ve sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1adf2-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="1adf2-268">Bu ayrıca yeni kullanır *dize ilişkilendirme* biçim dizesi çıkışı kolaylaştırır özelliği.</span><span class="sxs-lookup"><span data-stu-id="1adf2-268">It also makes use of the new *string interpolation* feature that makes it easier to format string output.</span></span>

<span data-ttu-id="1adf2-269">Yeni türünü kullanmak için başlangıç deste üreten sorgu güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="1adf2-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="1adf2-270">Derleme ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-270">Compile and run again.</span></span> <span data-ttu-id="1adf2-271">Çıktı biraz temizleyici ve kod biraz daha açıktır ve daha kolay genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="1adf2-272">Sonuç</span><span class="sxs-lookup"><span data-stu-id="1adf2-272">Conclusion</span></span>

<span data-ttu-id="1adf2-273">Bu örnek, LINQ kullanılan yöntemlerin bazıları gösterdi, kodu LINQ ile kolayca kullanılacak kendi yöntemleri oluşturmak nasıl etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="1adf2-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="1adf2-274">Bu ayrıca, yavaş ve istekli değerlendirme karar performans üzerinde olabilir etkileyen arasındaki farkları gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-274">It also showed you the differences between lazy and eager evaluation, and the affect that decision can have on performance.</span></span>

<span data-ttu-id="1adf2-275">Bir bit hakkında bir magician'ın tekniği de öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf2-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="1adf2-276">Burada, her kartı deste taşır kontrol sağladığından magicians faro karışık kullanın.</span><span class="sxs-lookup"><span data-stu-id="1adf2-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="1adf2-277">Bazı ipuçlarını magician deste en üstünde bir kart yerleştirin bir izleyici üyenin ve burada bu kartı gider bilerek birkaç kez seçimdeki.</span><span class="sxs-lookup"><span data-stu-id="1adf2-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="1adf2-278">Belirli bir yolla deste ayarlamak diğer İllüzyonları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1adf2-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="1adf2-279">Bir magician eli gerçekleştirmeden önce deste ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1adf2-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="1adf2-280">Ardından aynen 5 kez iç karışık kullanarak deste karışık.</span><span class="sxs-lookup"><span data-stu-id="1adf2-280">Then she will shuffle the deck 5 times using an inner shuffle.</span></span> <span data-ttu-id="1adf2-281">Aşama üzerinde aynen rastgele deste gibi göründüğünü göster, 3 kez daha karışık ve tam olarak nasıl istediği ayarlamak deste sahip.</span><span class="sxs-lookup"><span data-stu-id="1adf2-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
