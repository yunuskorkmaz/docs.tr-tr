---
title: "Hızlı Başlangıç - koleksiyonlar - C# Kılavuzu"
description: "C# bu hızlı başlangıç listesi koleksiyonunda inceleyerek öğrenin."
keywords: "C#, Get Started, öğretici, koleksiyonları listesi"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 44e79432c0a1970313cba21778e2bf439f8a4388
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="50b12-104">C# hızlı başlangıç: koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="50b12-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="50b12-105">Bu hızlı başlangıç C# dili ve temel bilgileri tanıtılmaktadır <xref:System.Collections.Generic.List%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="50b12-105">This quick start provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="50b12-106">Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="50b12-106">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="50b12-107">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="50b12-107">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="50b12-108">Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel hızlı başlangıçlar giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="50b12-108">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="50b12-109">Basit liste örnek.</span><span class="sxs-lookup"><span data-stu-id="50b12-109">A basic list example.</span></span>

<span data-ttu-id="50b12-110">Adlı bir dizin oluşturun **listesi Hızlı Başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="50b12-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="50b12-111">Geçerli dizin çalıştırma yapıp `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="50b12-111">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="50b12-112">Yalnızca tamamladıysanız [10 dakika içinde .NET ile çalışmaya başlama](https://www.microsoft.com/net), az önce oluşturduğunuz Uygulamam uygulamayı kullanmaya devam.</span><span class="sxs-lookup"><span data-stu-id="50b12-112">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>
 
<span data-ttu-id="50b12-113">Açık **Program.cs** sık kullanılan Düzenleyicisi ve var olan kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="50b12-113">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="50b12-114">Değiştir `<name>` adıyla.</span><span class="sxs-lookup"><span data-stu-id="50b12-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="50b12-115">Kaydet **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="50b12-115">Save **Program.cs**.</span></span> <span data-ttu-id="50b12-116">Tür `dotnet run` , konsol penceresinde deneyin.</span><span class="sxs-lookup"><span data-stu-id="50b12-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="50b12-117">Yalnızca dizelerinin listesini oluşturduğunuz, üç adları bu listeye eklenen ve tümü büyük harf adlarında çıkışı yazdırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="50b12-117">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="50b12-118">Listede ilerleyin döngü içinde daha önce hızlı başlatır, öğrendiğinize kavramları kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="50b12-118">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="50b12-119">Adlarını görüntülemek için kod kullanır **Ara değerli dizeler**.</span><span class="sxs-lookup"><span data-stu-id="50b12-119">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="50b12-120">Öncesinde ne zaman bir `string` ile `$` karakter dizesi bildiriminde C# kodu katıştırmak.</span><span class="sxs-lookup"><span data-stu-id="50b12-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="50b12-121">Gerçek dize, C# kodu ürettiği değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="50b12-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="50b12-122">Bu örnekte, yerini `{name.ToUpper()}` aradığınız çünkü her adıyla dönüştürülen büyük harfler için <xref:System.String.ToUpper%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50b12-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="50b12-123">Şimdi keşfetme tutun.</span><span class="sxs-lookup"><span data-stu-id="50b12-123">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="50b12-124">Liste içeriklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="50b12-124">Modify list contents</span></span>

<span data-ttu-id="50b12-125">Kullandığı oluşturduğunuz koleksiyonda <xref:System.Collections.Generic.List%601> türü.</span><span class="sxs-lookup"><span data-stu-id="50b12-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="50b12-126">Bu tür, öğelerin sıralarının depolar.</span><span class="sxs-lookup"><span data-stu-id="50b12-126">This type stores sequences of elements.</span></span> <span data-ttu-id="50b12-127">Açılı ayraçları arasında öğelerin türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="50b12-127">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="50b12-128">Bu önemli bir özelliği <xref:System.Collections.Generic.List%601> türüdür onu büyütür veya böylelikle küçültür, ekleme veya öğeleri kaldırma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50b12-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="50b12-129">Bu kodu kapatmadan önce ekleyin `}` içinde `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="50b12-129">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="50b12-130">İki daha fazla ad listesinin sonuna ekledik.</span><span class="sxs-lookup"><span data-stu-id="50b12-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="50b12-131">Ayrıca bir de kaldırdınız.</span><span class="sxs-lookup"><span data-stu-id="50b12-131">You've also removed one as well.</span></span> <span data-ttu-id="50b12-132">Dosya ve türü Kaydet `dotnet run` denemek üzere.</span><span class="sxs-lookup"><span data-stu-id="50b12-132">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="50b12-133"><xref:System.Collections.Generic.List%601> Tarafından ayrı öğeleri başvuru sağlar **dizin** de.</span><span class="sxs-lookup"><span data-stu-id="50b12-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="50b12-134">Dizin arasında yerleştirin `[` ve `]` listesi adından belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="50b12-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="50b12-135">C# 0 ilk dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50b12-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="50b12-136">Bu kodu eklediğiniz kodun hemen altına ekleyin ve deneyin:</span><span class="sxs-lookup"><span data-stu-id="50b12-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="50b12-137">Bir dizin listesi ötesinde erişemiyor.</span><span class="sxs-lookup"><span data-stu-id="50b12-137">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="50b12-138">Bu nedenle en büyük geçerli dizin biridir dizinlerini 0'da, başlangıç unutmayın listedeki öğeleri sayısından küçük.</span><span class="sxs-lookup"><span data-stu-id="50b12-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="50b12-139">Ne kadar süreyle listeyi kullanarak denetleyebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="50b12-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="50b12-140">Main yönteminin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="50b12-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="50b12-141">Dosya ve türü Kaydet `dotnet run` yeniden sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="50b12-141">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="50b12-142">Arama ve sıralama listeler</span><span class="sxs-lookup"><span data-stu-id="50b12-142">Search and sort lists</span></span>
<span data-ttu-id="50b12-143">Bizim örneklerimizi görece küçük listeleri kullanın, ancak uygulamalarınızı genellikle bazen binlerce numaralandırma pek çok daha fazla öğe ile listeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50b12-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="50b12-144">Bu büyük koleksiyonlarda öğeleri bulmak için farklı öğeleri listede arama gerekir.</span><span class="sxs-lookup"><span data-stu-id="50b12-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="50b12-145"><xref:System.Collections.Generic.List%601.IndexOf%2A> Yöntemi için bir öğe arar ve öğenin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="50b12-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="50b12-146">Bu kodu altına ekleyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="50b12-146">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
    
}
```

<span data-ttu-id="50b12-147">Listenizdeki öğeleri de sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="50b12-147">The items in your list can be sorted as well.</span></span> <span data-ttu-id="50b12-148"><xref:System.Collections.Generic.List%601.Sort%2A> Yöntemi (alfabetik olarak söz konusu olduğunda dizeleri) normal sıralarına listesindeki tüm öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="50b12-148">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="50b12-149">Bu kodu altına ekleyin bizim `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="50b12-149">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="50b12-150">Dosyayı kaydedip türü `dotnet run` bu en son sürümünü denemek için.</span><span class="sxs-lookup"><span data-stu-id="50b12-150">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="50b12-151">Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın.</span><span class="sxs-lookup"><span data-stu-id="50b12-151">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="50b12-152">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="50b12-152">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="50b12-153">Yeniden Adlandır, `Main` yönteme `WorkingWithStrings` ve yeni bir yazma `Main` çağıran yöntemi `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="50b12-153">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="50b12-154">İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="50b12-154">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="50b12-155">Diğer türleri listesi</span><span class="sxs-lookup"><span data-stu-id="50b12-155">Lists of other types</span></span>

<span data-ttu-id="50b12-156">Kullanmakta olduğunuz `string` kadarki listelerindeki türü.</span><span class="sxs-lookup"><span data-stu-id="50b12-156">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="50b12-157">Olalım bir <xref:System.Collections.Generic.List%601> farklı türü kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="50b12-157">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="50b12-158">Şimdi bir sayı kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50b12-158">Let's build a set of numbers.</span></span> 

<span data-ttu-id="50b12-159">Aşağıdaki yeni altına ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="50b12-159">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="50b12-160">Tamsayı listesi oluşturur ve ilk iki tamsayı 1 değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="50b12-160">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="50b12-161">İlk iki değerlerini bunlar bir *Fibonacci dizisi*, sayılardan oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="50b12-161">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="50b12-162">Sonraki her Fibonacci numarası, önceki iki sayı toplamı gerçekleştirerek bulunur.</span><span class="sxs-lookup"><span data-stu-id="50b12-162">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="50b12-163">Bu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="50b12-163">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="50b12-164">Dosyayı kaydedip türü `dotnet run` sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="50b12-164">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="50b12-165">Bu bölüm yalnızca yoğunlaşmak için çağıran kodu yorum yapabileceği `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="50b12-165">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="50b12-166">Yalnızca iki put `/` bu gibi karakterler çağrı önünde: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="50b12-166">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="50b12-167">sınama</span><span class="sxs-lookup"><span data-stu-id="50b12-167">Challenge</span></span>
<span data-ttu-id="50b12-168">Birlikte koyabilirsiniz varsa bkz bazı kavramlar bu ve önceki sürümleri dersleri.</span><span class="sxs-lookup"><span data-stu-id="50b12-168">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="50b12-169">Ne kadar Fibonacci numaralarıyla derlediğiniz genişletin.</span><span class="sxs-lookup"><span data-stu-id="50b12-169">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="50b12-170">İlk 20 sayıları sırayla oluşturmak için kod yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="50b12-170">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="50b12-171">(Bir ipucu olarak 20 Fibonacci 6765 numarasıdır.)</span><span class="sxs-lookup"><span data-stu-id="50b12-171">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="50b12-172">Tam sınama</span><span class="sxs-lookup"><span data-stu-id="50b12-172">Complete challenge</span></span>

<span data-ttu-id="50b12-173">Örnek bir çözüm tarafından görebilirsiniz [Github'da tamamlanmış örnek kodu incelemeden](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="50b12-173">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="50b12-174">Her döngü tekrarında ile son iki tamsayı listesinde, bunları birleşimi ve bu değer listesine ekleyerek yönlendiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="50b12-174">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="50b12-175">Listeye 20 öğeleri ekleyene kadar döngü tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="50b12-175">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="50b12-176">Tebrikler, liste hızlı başlangıç tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="50b12-176">Congratulations, you've completed the list quick start.</span></span> <span data-ttu-id="50b12-177">İle devam edebilirsiniz [sınıfları giriş](introduction-to-classes.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="50b12-177">You can continue with the [Introduction to classes](introduction-to-classes.md) quick start in your own development environment.</span></span>

<span data-ttu-id="50b12-178">İle çalışma hakkında daha fazla bilgiyi `List` yazın [.NET Kılavuzu](../../standard/index.md) konuyla ilgili [koleksiyonları](../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="50b12-178">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="50b12-179">Ayrıca diğer birçok koleksiyon türleri hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="50b12-179">You'll also learn about many other collection types.</span></span>
