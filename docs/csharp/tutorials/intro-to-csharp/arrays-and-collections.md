---
title: Koleksiyonlar - giriş çalışın C# Öğreticisi
description: Bilgi C# liste koleksiyonu bu öğreticideki keşfetmeye tarafından.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 9a910ccd6265011fc0e5540b461ba089dbd3e7ba
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261277"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="10a7a-103">Veri koleksiyonları genel liste türünü kullanarak yönetmeyi öğrenin</span><span class="sxs-lookup"><span data-stu-id="10a7a-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="10a7a-104">Bu giriş niteliğindeki öğretici tanıtır C# dili ve temel <xref:System.Collections.Generic.List%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="10a7a-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="10a7a-105">Bu öğretici geliştirme için kullanabileceğiniz bir makine olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="10a7a-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="10a7a-106">.NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="10a7a-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="10a7a-107">Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md), daha fazla bilgi için bağlantılarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="10a7a-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="10a7a-108">Temel listesi örneği</span><span class="sxs-lookup"><span data-stu-id="10a7a-108">A basic list example</span></span>

<span data-ttu-id="10a7a-109">Adlı bir dizin oluşturmak **liste-tutorial**.</span><span class="sxs-lookup"><span data-stu-id="10a7a-109">Create a directory named **list-tutorial**.</span></span> <span data-ttu-id="10a7a-110">Geçerli dizin ve çalışma olun `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="10a7a-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="10a7a-111">Açık **Program.cs** sık kullandığınız düzenleyicide ve varolan kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="10a7a-111">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

<span data-ttu-id="10a7a-112">Değiştirin `<name>` adınızla.</span><span class="sxs-lookup"><span data-stu-id="10a7a-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="10a7a-113">Kaydet **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="10a7a-113">Save **Program.cs**.</span></span> <span data-ttu-id="10a7a-114">Tür `dotnet run` konsol pencerenizde denemek için.</span><span class="sxs-lookup"><span data-stu-id="10a7a-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="10a7a-115">Yalnızca bir dize listesi oluşturduğunuz, üç adları bu listeye eklenmesine ve tamamı büyük harf adları kullanıma yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="10a7a-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="10a7a-116">Önceki öğreticilerde listede döngü öğrendiniz kavramları kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="10a7a-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="10a7a-117">Görünen adları için kodu kullanır [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="10a7a-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="10a7a-118">Ne zaman önünde bir `string` ile `$` karakter dizesi bildiriminde C# kod ekleme.</span><span class="sxs-lookup"><span data-stu-id="10a7a-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="10a7a-119">Gerçek dize, C# kodu ürettiği değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="10a7a-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="10a7a-120">Bu örnekte, onu değiştirir `{name.ToUpper()}` her addaki aradığınız çünkü harfleri büyük olacak şekilde dönüştürülmüş <xref:System.String.ToUpper%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="10a7a-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="10a7a-121">Şimdi keşfetmeye devam etmek.</span><span class="sxs-lookup"><span data-stu-id="10a7a-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="10a7a-122">Liste içeriklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="10a7a-122">Modify list contents</span></span>

<span data-ttu-id="10a7a-123">Kullanan oluşturduğunuz koleksiyonda <xref:System.Collections.Generic.List%601> türü.</span><span class="sxs-lookup"><span data-stu-id="10a7a-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="10a7a-124">Bu tür, öğelerin sıralarının depolar.</span><span class="sxs-lookup"><span data-stu-id="10a7a-124">This type stores sequences of elements.</span></span> <span data-ttu-id="10a7a-125">Açılı ayraçlar arasındaki öğelerin türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="10a7a-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="10a7a-126">Bu önemli bir özelliği <xref:System.Collections.Generic.List%601> türüdür bunu büyüyebilen veya küçülebilen, ekleme veya öğeleri kaldırma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10a7a-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="10a7a-127">Kapatmadan önce bu kodu ekleyin `}` içinde `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="10a7a-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="10a7a-128">Listenin sonuna iki daha fazla ad ekledik.</span><span class="sxs-lookup"><span data-stu-id="10a7a-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="10a7a-129">Ayrıca bir de kaldırdınız.</span><span class="sxs-lookup"><span data-stu-id="10a7a-129">You've also removed one as well.</span></span> <span data-ttu-id="10a7a-130">Dosya ve tür kaydetme `dotnet run` denemek için.</span><span class="sxs-lookup"><span data-stu-id="10a7a-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="10a7a-131"><xref:System.Collections.Generic.List%601> Tek tek öğeler tarafından başvuruda sayesinde **dizin** de.</span><span class="sxs-lookup"><span data-stu-id="10a7a-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="10a7a-132">Arasında dizine yerleştirdiğiniz `[` ve `]` liste adı aşağıdaki belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="10a7a-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="10a7a-133">C#0 için ilk dizinini kullanır.</span><span class="sxs-lookup"><span data-stu-id="10a7a-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="10a7a-134">Yeni eklediğiniz kodun hemen altına bu kodu ekleyin ve deneyin:</span><span class="sxs-lookup"><span data-stu-id="10a7a-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="10a7a-135">Bir dizin listesi ötesinde erişemez.</span><span class="sxs-lookup"><span data-stu-id="10a7a-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="10a7a-136">En büyük geçerli dizin olduğundan dizinleri 0'da başlar unutmayın listedeki öğelerin sayısından küçük.</span><span class="sxs-lookup"><span data-stu-id="10a7a-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="10a7a-137">Listenin ne kadar süre kullandığı denetleyebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="10a7a-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="10a7a-138">Main yönteminin sonunda aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="10a7a-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="10a7a-139">Dosya ve tür kaydetme `dotnet run` yeniden sonuçları görmek için.</span><span class="sxs-lookup"><span data-stu-id="10a7a-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="10a7a-140">Arama ve sıralama listeler</span><span class="sxs-lookup"><span data-stu-id="10a7a-140">Search and sort lists</span></span>

<span data-ttu-id="10a7a-141">Örneklerimizi görece küçük listeleri kullanın, ancak uygulamalarınızın genellikle bazen bin numaralandırma çok daha fazla öğe ile listeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10a7a-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="10a7a-142">İçinde büyük bu koleksiyonlara öğeleri bulmak için farklı öğeler listesinde arama yapmanız gerekmiyor.</span><span class="sxs-lookup"><span data-stu-id="10a7a-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="10a7a-143"><xref:System.Collections.Generic.List%601.IndexOf%2A> Yöntemi bir öğe için arar ve öğenin indisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="10a7a-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="10a7a-144">Bu kodu altına ekleyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="10a7a-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="10a7a-145">Listenizdeki öğeleri de sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="10a7a-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="10a7a-146"><xref:System.Collections.Generic.List%601.Sort%2A> Yöntemi (alfabetik sırada durumunda dizeler) normal sıralarına listesinden tüm öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="10a7a-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="10a7a-147">Bu kod bölmenizin altına eklemek bizim `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="10a7a-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="10a7a-148">Dosya ve tür Kaydet `dotnet run` en son sürümü denemek için.</span><span class="sxs-lookup"><span data-stu-id="10a7a-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="10a7a-149">Sonraki bölümde başlamadan önce geçerli kodu ayrı bir yöntem geçelim.</span><span class="sxs-lookup"><span data-stu-id="10a7a-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="10a7a-150">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="10a7a-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="10a7a-151">Yeniden adlandırma, `Main` yönteme `WorkingWithStrings` ve yeni bir yazma `Main` metoduna çağrı yapan `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="10a7a-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="10a7a-152">İşiniz bittiğinde, kodunuzun şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="10a7a-152">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

## <a name="lists-of-other-types"></a><span data-ttu-id="10a7a-153">Diğer türleri listesi</span><span class="sxs-lookup"><span data-stu-id="10a7a-153">Lists of other types</span></span>

<span data-ttu-id="10a7a-154">Kullanmakta olduğunuz `string` şimdiye listelerindeki türü.</span><span class="sxs-lookup"><span data-stu-id="10a7a-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="10a7a-155">Olalım bir <xref:System.Collections.Generic.List%601> kullanarak farklı bir tür.</span><span class="sxs-lookup"><span data-stu-id="10a7a-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="10a7a-156">Bir dizi sayının oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="10a7a-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="10a7a-157">Aşağıdaki yeni altına ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="10a7a-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="10a7a-158">Tamsayı listesi oluşturur ve ilk iki tamsayı 1 değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="10a7a-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="10a7a-159">İlk iki değerlerini bunlar bir *Fibonacci dizisi*, bir sayı dizisi üzerinde.</span><span class="sxs-lookup"><span data-stu-id="10a7a-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="10a7a-160">Önceki iki sayının toplamı gerçekleştirerek sonraki her Fibonacci numarası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="10a7a-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="10a7a-161">Bu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="10a7a-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="10a7a-162">Dosya ve tür Kaydet `dotnet run` sonuçları görmek için.</span><span class="sxs-lookup"><span data-stu-id="10a7a-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="10a7a-163">Bu bölümde üzerinde yoğunlaşmak için çağıran kodu yorum yapabilecek `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="10a7a-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="10a7a-164">Yalnızca iki yerleştirme `/` bu gibi karakterler çağrısının önünde: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="10a7a-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="10a7a-165">Sınama</span><span class="sxs-lookup"><span data-stu-id="10a7a-165">Challenge</span></span>

<span data-ttu-id="10a7a-166">Birlikte koyabilirsiniz varsa bkz. bazı kavramlar ve daha önce bu dersler.</span><span class="sxs-lookup"><span data-stu-id="10a7a-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="10a7a-167">Ne kadar Fibonacci numaralarıyla derlediğiniz genişletin.</span><span class="sxs-lookup"><span data-stu-id="10a7a-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="10a7a-168">Dizideki ilk 20 sayılar üretmek için kod yazmak bu seçeneği deneyin.</span><span class="sxs-lookup"><span data-stu-id="10a7a-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="10a7a-169">(Bir ipucu olarak 20 Fibonacci 6765 numarasıdır.)</span><span class="sxs-lookup"><span data-stu-id="10a7a-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="10a7a-170">Görevi tamamlama</span><span class="sxs-lookup"><span data-stu-id="10a7a-170">Complete challenge</span></span>

<span data-ttu-id="10a7a-171">Örnek bir çözüm tarafından gördüğünüz [tamamlanan örnek koda Github'da bakmak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="10a7a-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="10a7a-172">Döngünün her yinelemesinden son iki tamsayının listesinde, bunları fiyatının ve bu değer, listeye eklemeyi yönlendiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="10a7a-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="10a7a-173">20 öğe listesine ekleyene kadar döngü tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="10a7a-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="10a7a-174">Tebrikler, liste öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="10a7a-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="10a7a-175">İle devam edebilir [sınıflara giriş](introduction-to-classes.md) kendi geliştirme ortamınızda öğretici.</span><span class="sxs-lookup"><span data-stu-id="10a7a-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="10a7a-176">İle çalışma hakkında daha fazla bilgi `List` yazın [.NET Kılavuzu](../../../standard/index.md) konuda [koleksiyonları](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="10a7a-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="10a7a-177">Ayrıca diğer birçok koleksiyon türleri hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="10a7a-177">You'll also learn about many other collection types.</span></span>