---
title: Koleksiyonlarla çalışma - C# eğitimine giriş
description: Bu öğreticide Liste koleksiyonunu inceleyerek C# öğrenin.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 554a4601157a7d4b873c22a46ee72b6601fc36d7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635657"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="308bb-103">Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin</span><span class="sxs-lookup"><span data-stu-id="308bb-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="308bb-104">Bu giriş öğretici c# dili ve <xref:System.Collections.Generic.List%601> sınıfın temelleri için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="308bb-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="308bb-105">Bu öğretici, geliştirme için kullanabileceğiniz bir makineye sahip olmak için bekliyor.</span><span class="sxs-lookup"><span data-stu-id="308bb-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="308bb-106">.NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.</span><span class="sxs-lookup"><span data-stu-id="308bb-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="308bb-107">Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md)dır.</span><span class="sxs-lookup"><span data-stu-id="308bb-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="308bb-108">Temel bir liste örneği</span><span class="sxs-lookup"><span data-stu-id="308bb-108">A basic list example</span></span>

<span data-ttu-id="308bb-109">*Liste öğretici*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="308bb-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="308bb-110">Geçerli dizini ve çalıştır `dotnet new console`ın.</span><span class="sxs-lookup"><span data-stu-id="308bb-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="308bb-111">Sık kullanılan düzenleyicide *Program.cs* açın ve varolan kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="308bb-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="308bb-112">Adınız ile değiştirin. `<name>`</span><span class="sxs-lookup"><span data-stu-id="308bb-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="308bb-113">*Program.cs* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="308bb-113">Save *Program.cs*.</span></span> <span data-ttu-id="308bb-114">Denemek `dotnet run` için konsol pencerenizi yazın.</span><span class="sxs-lookup"><span data-stu-id="308bb-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="308bb-115">Dizeleri bir liste oluşturdunuz, bu listeye üç ad eklediniz ve tüm CAPS'lerde adları yazdırdın.</span><span class="sxs-lookup"><span data-stu-id="308bb-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="308bb-116">Listeyi gözden geçirmek için önceki öğreticilerde öğrendiğiniz kavramları kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="308bb-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="308bb-117">Adları görüntülemek için kod [dize enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="308bb-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="308bb-118">`$` Karakterle bir `string` önce olduğunuzda, dize bildirimine C# kodunu katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="308bb-119">Gerçek dize, c# kodunu oluşturduğu değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="308bb-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="308bb-120">Bu örnekte, `{name.ToUpper()}` <xref:System.String.ToUpper%2A> yöntemi çağırdığınız için büyük harfe dönüştürülen her adla değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="308bb-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="308bb-121">Keşfetmeye devam edelim.</span><span class="sxs-lookup"><span data-stu-id="308bb-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="308bb-122">Liste içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="308bb-122">Modify list contents</span></span>

<span data-ttu-id="308bb-123">Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="308bb-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="308bb-124">Bu tür öğelerin dizileri depolar.</span><span class="sxs-lookup"><span data-stu-id="308bb-124">This type stores sequences of elements.</span></span> <span data-ttu-id="308bb-125">Açı braketleri arasındaki öğelerin türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="308bb-126">Bu <xref:System.Collections.Generic.List%601> türün önemli bir yönü, öğeleri eklemenize veya kaldırmanıza olanak sağlayarak büyüyebilir veya küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="308bb-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="308bb-127">`Main` Yöntemde kapanışönce `}` bu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="308bb-128">Listenin sonuna iki ad daha eklediniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="308bb-129">Bir tanesini de kaldırdın.</span><span class="sxs-lookup"><span data-stu-id="308bb-129">You've also removed one as well.</span></span> <span data-ttu-id="308bb-130">Dosyayı kaydedin `dotnet run` ve denemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="308bb-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="308bb-131"><xref:System.Collections.Generic.List%601> Dizin bazında tek tek **index** öğelere başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="308bb-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="308bb-132">Dizini liste `[` adını `]` izleyen belirteçler arasına yerebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="308bb-133">C# ilk dizin için 0 kullanır.</span><span class="sxs-lookup"><span data-stu-id="308bb-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="308bb-134">Bu kodu eklediğiniz kodun hemen altına ekleyin ve deneyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="308bb-135">Listenin sonundan sonra bir dizin erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="308bb-136">Endekslerin 0'dan başladığını unutmayın, bu nedenle en büyük geçerli dizin listedeki öğe sayısından bir azdır.</span><span class="sxs-lookup"><span data-stu-id="308bb-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="308bb-137">Listenin <xref:System.Collections.Generic.List%601.Count%2A> özelliği ne kadar süreyle kullandığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="308bb-138">Ana yöntemin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="308bb-139">Dosyayı kaydedin `dotnet run` ve sonuçları görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="308bb-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="308bb-140">Listeleri arama ve sıralama</span><span class="sxs-lookup"><span data-stu-id="308bb-140">Search and sort lists</span></span>

<span data-ttu-id="308bb-141">Örneklerimiz nispeten küçük listeler kullanır, ancak uygulamalarınız genellikle daha fazla öğeiçeren listeler oluşturabilir ve bazen binlercesini numaralandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="308bb-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="308bb-142">Bu büyük koleksiyonlarda öğeleri bulmak için, farklı öğeler için listearama nız gerekir.</span><span class="sxs-lookup"><span data-stu-id="308bb-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="308bb-143">Yöntem <xref:System.Collections.Generic.List%601.IndexOf%2A> bir öğeyi arar ve öğenin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="308bb-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="308bb-144">Bu kodu yönteminizin `Main` altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-144">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="308bb-145">Listenizdeki öğeler de sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="308bb-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="308bb-146">Yöntem, <xref:System.Collections.Generic.List%601.Sort%2A> listedeki tüm öğeleri normal sıralarına göre sıralar (dizeleri durumunda alfabetik olarak).</span><span class="sxs-lookup"><span data-stu-id="308bb-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="308bb-147">Bu kodu yöntemimizin `Main` altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="308bb-148">Bu son sürümü `dotnet run` denemek için dosyayı kaydedin ve yazın.</span><span class="sxs-lookup"><span data-stu-id="308bb-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="308bb-149">Bir sonraki bölümü başlatmadan önce, geçerli kodu ayrı bir yönteme taşıyalım.</span><span class="sxs-lookup"><span data-stu-id="308bb-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="308bb-150">Bu, yeni bir örnekle çalışmaya başlamayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="308bb-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="308bb-151">Metodunuzu `WorkingWithStrings` yeniden adlandırın `Main` `Main` ve `WorkingWithStrings`çağıran yeni bir yöntem yazın.</span><span class="sxs-lookup"><span data-stu-id="308bb-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="308bb-152">Bitirdikten sonra, kodunuz şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="308bb-152">When you have finished, your code should look like this:</span></span>

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

        static void WorkingWithStrings()
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
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="308bb-153">Diğer türler deki listeler</span><span class="sxs-lookup"><span data-stu-id="308bb-153">Lists of other types</span></span>

<span data-ttu-id="308bb-154">Şu ana kadar `string` listelerdeki türü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="308bb-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="308bb-155">Farklı bir <xref:System.Collections.Generic.List%601> tür kullanarak yapalım.</span><span class="sxs-lookup"><span data-stu-id="308bb-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="308bb-156">Bir dizi sayı oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="308bb-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="308bb-157">Yeni `Main` yönteminizin altına aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="308bb-158">Bu, tamsayılar listesi oluşturur ve ilk iki tamsayıdeğerini 1 değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="308bb-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="308bb-159">Bunlar *fibonacci dizisinin*ilk iki değeridir, bir sayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="308bb-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="308bb-160">Sonraki her Fibonacci numarası önceki iki sayının toplamı alınarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="308bb-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="308bb-161">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="308bb-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="308bb-162">Sonuçları görmek için `dotnet run` dosyayı kaydedin ve yazın.</span><span class="sxs-lookup"><span data-stu-id="308bb-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="308bb-163">Sadece bu bölüme odaklanmak için, çağıran `WorkingWithStrings();`kodu yorumlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="308bb-164">Sadece bu `/` gibi arama önünde iki karakter `// WorkingWithStrings();`koyun: .</span><span class="sxs-lookup"><span data-stu-id="308bb-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="308bb-165">Sınama</span><span class="sxs-lookup"><span data-stu-id="308bb-165">Challenge</span></span>

<span data-ttu-id="308bb-166">Bu ve daha önceki derslerden bazı kavramları bir araya getirebilecek olup olmadığını görün.</span><span class="sxs-lookup"><span data-stu-id="308bb-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="308bb-167">Fibonacci Numbers ile şimdiye kadar inşa ettiğiniz şeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="308bb-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="308bb-168">Dizideki ilk 20 sayıyı oluşturmak için kodu yazmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="308bb-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="308bb-169">(İpucu olarak, 20 Fibonacci sayısı 6765'tir.)</span><span class="sxs-lookup"><span data-stu-id="308bb-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="308bb-170">Görevi tamamlama</span><span class="sxs-lookup"><span data-stu-id="308bb-170">Complete challenge</span></span>

<span data-ttu-id="308bb-171">[GitHub'da bitmiş örnek koduna bakarak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)örnek bir çözüm görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="308bb-172">Döngünün her yinelemesinde, listedeki son iki sondayı alıp, bunları özetliyor ve bu değeri listeye ekliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="308bb-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="308bb-173">Listeye 20 öğe ekleyene kadar döngü yineler.</span><span class="sxs-lookup"><span data-stu-id="308bb-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="308bb-174">Tebrikler, liste eğitimini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="308bb-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="308bb-175">Kendi geliştirme ortamınızda [sınıflara Giriş](introduction-to-classes.md) eğitimi ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="308bb-176">[Koleksiyonlarla](../../../standard/collections/index.md)ilgili [.NET](../../../standard/index.yml) `List` kılavuz makalesinde türüyle çalışma hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-176">You can learn more about working with the `List` type in the [.NET guide](../../../standard/index.yml) article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="308bb-177">Ayrıca diğer birçok koleksiyon türü hakkında da bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="308bb-177">You'll also learn about many other collection types.</span></span>
