---
title: Koleksiyonlarla çalışma-C# öğreticisine giriş
description: Bu öğreticide liste koleksiyonunu inceleyerek C# öğrenin.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: e2282df21420630634911e07f4fb3b94f34a792b
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414689"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="925a6-103">Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin</span><span class="sxs-lookup"><span data-stu-id="925a6-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="925a6-104">Bu giriş öğreticisi, C# diline ve sınıfının temel bilgilerine bir giriş sağlar <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="925a6-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="925a6-105">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="925a6-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="925a6-106">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="925a6-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="925a6-107">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı bağlantılarıyla birlikte [geliştirme araçları hakkında bilgi sahibi](local-environment.md)olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="925a6-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="925a6-108">Temel liste örneği</span><span class="sxs-lookup"><span data-stu-id="925a6-108">A basic list example</span></span>

<span data-ttu-id="925a6-109">*List-öğreticisi*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="925a6-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="925a6-110">Geçerli dizini oluşturun ve çalıştırın `dotnet new console` .</span><span class="sxs-lookup"><span data-stu-id="925a6-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="925a6-111">En sevdiğiniz düzenleyicide *program.cs* açın ve mevcut kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="925a6-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="925a6-112">`<name>`Adınızla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="925a6-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="925a6-113">*Program.cs* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="925a6-113">Save *Program.cs*.</span></span> <span data-ttu-id="925a6-114">`dotnet run`Denemek için konsol pencerenizi yazın.</span><span class="sxs-lookup"><span data-stu-id="925a6-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="925a6-115">Dizelerin bir listesini oluşturdunuz, bu listeye üç ad eklediniz ve adları tüm büyük harfler halinde yazdırdık.</span><span class="sxs-lookup"><span data-stu-id="925a6-115">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="925a6-116">Önceki öğreticilerde, listede döngü gerçekleştirmek için öğrenmiş olduğunuz kavramları kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="925a6-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="925a6-117">Adları görüntülenecek kod, [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="925a6-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="925a6-118">Bir `string` `$` karakterden önce karakterinden sonra, C# kodunu dize bildirimine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="925a6-119">Gerçek dize, bu C# kodunun oluşturduğu değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="925a6-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="925a6-120">Bu örnekte, yöntemini çağırdığı için, her bir adla ' ı, `{name.ToUpper()}` büyük harflere dönüştürülecek şekilde değiştirir <xref:System.String.ToUpper%2A> .</span><span class="sxs-lookup"><span data-stu-id="925a6-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="925a6-121">Araştırma devam edelim.</span><span class="sxs-lookup"><span data-stu-id="925a6-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="925a6-122">Liste içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="925a6-122">Modify list contents</span></span>

<span data-ttu-id="925a6-123">Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="925a6-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="925a6-124">Bu tür öğe dizilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="925a6-124">This type stores sequences of elements.</span></span> <span data-ttu-id="925a6-125">Açılı ayraçlar arasındaki öğelerin türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="925a6-126">Bu türün önemli bir yönü <xref:System.Collections.Generic.List%601> büyümenin veya küçülebileceği, öğe eklemenize veya kaldırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="925a6-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="925a6-127">Yöntemdeki kapatmadan önce bu kodu ekleyin `}` `Main` :</span><span class="sxs-lookup"><span data-stu-id="925a6-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="925a6-128">Listenin sonuna iki ad daha eklediniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="925a6-129">Ayrıca bir tane de kaldırmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="925a6-129">You've also removed one as well.</span></span> <span data-ttu-id="925a6-130">Dosyayı kaydedin ve `dotnet run` denemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="925a6-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="925a6-131">, <xref:System.Collections.Generic.List%601> Tek tek öğeleri **dizine** göre de başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="925a6-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="925a6-132">Dizini, `[` `]` liste adını izleyen ve belirteçleri arasına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="925a6-133">C# ilk dizin için 0 kullanır.</span><span class="sxs-lookup"><span data-stu-id="925a6-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="925a6-134">Bu kodu, yeni eklediğiniz kodun hemen altına ekleyin ve deneyin:</span><span class="sxs-lookup"><span data-stu-id="925a6-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="925a6-135">Liste sonunun ötesinde bir dizine erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-135">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="925a6-136">Dizinlerin 0 ' dan başlayıp, en büyük geçerli dizinin listedeki öğe sayısından bir daha az olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="925a6-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="925a6-137">Listenin özelliğini ne kadar süreyle kullandığını kontrol edebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> .</span><span class="sxs-lookup"><span data-stu-id="925a6-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="925a6-138">Main yönteminin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="925a6-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="925a6-139">Dosyayı kaydedin ve `dotnet run` sonuçları görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="925a6-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="925a6-140">Arama ve sıralama listeleri</span><span class="sxs-lookup"><span data-stu-id="925a6-140">Search and sort lists</span></span>

<span data-ttu-id="925a6-141">Örneklerimizde görece küçük listeler kullanılıyor, ancak uygulamalarınız genellikle binlerce numaralandırma olan çok sayıda öğesi olan listeler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="925a6-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="925a6-142">Bu daha büyük koleksiyonlardaki öğeleri bulmak için listede farklı öğeler için arama yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="925a6-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="925a6-143"><xref:System.Collections.Generic.List%601.IndexOf%2A>Yöntemi bir öğe arar ve öğenin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="925a6-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="925a6-144">Öğe listede yoksa, `IndexOf` döndürür `-1` .</span><span class="sxs-lookup"><span data-stu-id="925a6-144">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="925a6-145">Bu kodu yönteminizin en altına ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="925a6-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="925a6-146">Listenizdeki öğeler de sıralanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="925a6-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="925a6-147"><xref:System.Collections.Generic.List%601.Sort%2A>Yöntemi, listedeki tüm öğeleri normal sıralarına göre sıralar (dizeler için alfabetik olarak).</span><span class="sxs-lookup"><span data-stu-id="925a6-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="925a6-148">Bu kodu yönteminizin en altına ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="925a6-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="925a6-149">`dotnet run`Bu en son sürümü denemek için dosyayı kaydedin ve yazın.</span><span class="sxs-lookup"><span data-stu-id="925a6-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="925a6-150">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="925a6-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="925a6-151">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="925a6-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="925a6-152">`Main`Yönteminizi olarak yeniden adlandırın `WorkingWithStrings` ve çağıran yeni bir `Main` Yöntem yazın `WorkingWithStrings` .</span><span class="sxs-lookup"><span data-stu-id="925a6-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="925a6-153">İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="925a6-153">When you've finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="925a6-154">Diğer türlerin listeleri</span><span class="sxs-lookup"><span data-stu-id="925a6-154">Lists of other types</span></span>

<span data-ttu-id="925a6-155">`string`Şu ana kadar listelerdeki türü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="925a6-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="925a6-156"><xref:System.Collections.Generic.List%601>Farklı bir tür kullanalım.</span><span class="sxs-lookup"><span data-stu-id="925a6-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="925a6-157">Bir sayı kümesi oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="925a6-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="925a6-158">Aşağıdakileri yeni yönteminizin altına ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="925a6-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="925a6-159">Bu, tamsayıların bir listesini oluşturur ve ilk iki tamsayının değerini 1 değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="925a6-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="925a6-160">Bunlar bir *Fibonaccı sırasının*ilk iki değeri, bir dizi sayı.</span><span class="sxs-lookup"><span data-stu-id="925a6-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="925a6-161">Her bir sonraki Fibonaccı numarası, önceki iki sayının toplamı alınarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="925a6-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="925a6-162">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="925a6-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="925a6-163">Sonuçları görmek için dosyayı kaydedin ve yazın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="925a6-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="925a6-164">Yalnızca bu bölüme odaklanmak için, çağıran kodu açıklama olarak ayarlayabilirsiniz `WorkingWithStrings();` .</span><span class="sxs-lookup"><span data-stu-id="925a6-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="925a6-165">`/`Çağrının önüne şu şekilde iki karakter koymanız yeterlidir: `// WorkingWithStrings();` .</span><span class="sxs-lookup"><span data-stu-id="925a6-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="925a6-166">Sınama</span><span class="sxs-lookup"><span data-stu-id="925a6-166">Challenge</span></span>

<span data-ttu-id="925a6-167">Bu ve önceki derslerden bazılarını bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="925a6-168">Fibonaccı numaralarına en fazla ne kadar derlediğiniz hakkında ' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="925a6-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="925a6-169">Dizideki ilk 20 sayıyı oluşturmak için kodu yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="925a6-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="925a6-170">(İpucu olarak, 20 fibonaccı numarası 6765 ' dir.)</span><span class="sxs-lookup"><span data-stu-id="925a6-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="925a6-171">Görevi tamamlama</span><span class="sxs-lookup"><span data-stu-id="925a6-171">Complete challenge</span></span>

<span data-ttu-id="925a6-172">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)örnek bir çözüm görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="925a6-173">Döngünün her tekrarında, listedeki son iki tamsayının yerine getiriyorsunuz ve bu değeri listeye ekliyor olursunuz.</span><span class="sxs-lookup"><span data-stu-id="925a6-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="925a6-174">Döngü, listeye 20 öğe ekleyinceye kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="925a6-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="925a6-175">Tebrikler, liste öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="925a6-175">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="925a6-176">Kendi geliştirme ortamınızda [sınıflarla tanışın](introduction-to-classes.md) öğreticisine devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-176">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="925a6-177">`List` [Koleksiyonlar](../../../standard/collections/index.md)üzerinde .net temelleri makalesindeki türle çalışma hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-177">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="925a6-178">Diğer birçok koleksiyon türünü de öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="925a6-178">You'll also learn about many other collection types.</span></span>
