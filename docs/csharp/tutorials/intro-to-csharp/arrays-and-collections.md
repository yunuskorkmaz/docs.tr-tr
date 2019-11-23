---
title: Koleksiyonlarla çalışma- C# öğreticiye giriş
description: Bu C# öğreticide liste koleksiyonunu inceleyerek öğrenin.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: b80225cf1614a7c25ac9011acd39e74032465ca3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834142"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="f6126-103">Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin</span><span class="sxs-lookup"><span data-stu-id="f6126-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="f6126-104">Bu giriş öğreticisi, C# dile ve <xref:System.Collections.Generic.List%601> sınıfının temel bilgilerine bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6126-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="f6126-105">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="f6126-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="f6126-106">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="f6126-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="f6126-107">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı bağlantılarıyla birlikte [geliştirme araçları hakkında bilgi sahibi](local-environment.md)olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6126-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="f6126-108">Temel liste örneği</span><span class="sxs-lookup"><span data-stu-id="f6126-108">A basic list example</span></span>

<span data-ttu-id="f6126-109">*List-öğreticisi*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6126-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="f6126-110">Geçerli dizini yapıp `dotnet new console`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f6126-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="f6126-111">En sevdiğiniz düzenleyicide *program.cs* açın ve mevcut kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f6126-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="f6126-112">`<name>`, adınızla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f6126-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="f6126-113">*Program.cs*Kaydet.</span><span class="sxs-lookup"><span data-stu-id="f6126-113">Save *Program.cs*.</span></span> <span data-ttu-id="f6126-114">Denemek için konsol pencerenize `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="f6126-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="f6126-115">Yalnızca bir dize listesi oluşturdunuz, bu listeye üç ad ekledik ve adları tüm büyük harfler içinde yazdırdınız.</span><span class="sxs-lookup"><span data-stu-id="f6126-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="f6126-116">Önceki öğreticilerde, listede döngü gerçekleştirmek için öğrenmiş olduğunuz kavramları kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f6126-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="f6126-117">Adları görüntülenecek kod, [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6126-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="f6126-118">Bir `string` `$` karakteri ile önce kullandığınızda, C# kodu String bildiriminde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="f6126-119">Gerçek dize, bu C# kodun oluşturduğu değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f6126-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="f6126-120">Bu örnekte, <xref:System.String.ToUpper%2A> yöntemini çağırdığı için `{name.ToUpper()}` her bir adla değiştirir ve büyük harflere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f6126-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="f6126-121">Araştırma devam edelim.</span><span class="sxs-lookup"><span data-stu-id="f6126-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="f6126-122">Liste içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="f6126-122">Modify list contents</span></span>

<span data-ttu-id="f6126-123">Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6126-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="f6126-124">Bu tür öğe dizilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="f6126-124">This type stores sequences of elements.</span></span> <span data-ttu-id="f6126-125">Açılı ayraçlar arasındaki öğelerin türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="f6126-126">Bu <xref:System.Collections.Generic.List%601> türünün önemli bir yönü büyümenin veya küçülebileceği, böylece öğe eklemenize veya kaldırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f6126-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="f6126-127">`Main` yönteminde kapanış `}` önce bu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="f6126-128">Listenin sonuna iki ad daha eklediniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="f6126-129">Ayrıca bir tane de kaldırmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f6126-129">You've also removed one as well.</span></span> <span data-ttu-id="f6126-130">Dosyayı kaydedin ve `dotnet run` yazarak deneyin.</span><span class="sxs-lookup"><span data-stu-id="f6126-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="f6126-131"><xref:System.Collections.Generic.List%601>, tek tek öğeleri **dizine** göre de başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6126-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="f6126-132">Dizini liste adından sonra `[` ve `]` belirteçleri arasına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="f6126-133">C#ilk dizin için 0 kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6126-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="f6126-134">Bu kodu, yeni eklediğiniz kodun hemen altına ekleyin ve deneyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="f6126-135">Liste sonunun ötesinde bir dizine erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="f6126-136">Dizinlerin 0 ' dan başlayıp, en büyük geçerli dizinin listedeki öğe sayısından bir daha az olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f6126-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="f6126-137">Listenin <xref:System.Collections.Generic.List%601.Count%2A> özelliğini ne kadar süreyle kullandığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="f6126-138">Main yönteminin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="f6126-139">Dosyayı kaydedin ve sonuçları görmek için `dotnet run` yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="f6126-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="f6126-140">Arama ve sıralama listeleri</span><span class="sxs-lookup"><span data-stu-id="f6126-140">Search and sort lists</span></span>

<span data-ttu-id="f6126-141">Örneklerimizde görece küçük listeler kullanılıyor, ancak uygulamalarınız genellikle binlerce numaralandırma olan çok sayıda öğesi olan listeler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f6126-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="f6126-142">Bu daha büyük koleksiyonlardaki öğeleri bulmak için listede farklı öğeler için arama yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6126-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="f6126-143"><xref:System.Collections.Generic.List%601.IndexOf%2A> yöntemi bir öğe arar ve öğenin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6126-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="f6126-144">Bu kodu `Main` yönteminizin en altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="f6126-145">Listenizdeki öğeler de sıralanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6126-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="f6126-146"><xref:System.Collections.Generic.List%601.Sort%2A> yöntemi, listedeki tüm öğeleri normal sıralarına göre sıralar (dizeler söz konusu olduğunda alfabetik olarak).</span><span class="sxs-lookup"><span data-stu-id="f6126-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="f6126-147">Bu kodu `Main` yönteminizin en altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="f6126-148">Bu en son sürümü denemek için dosyayı kaydedin ve `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="f6126-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="f6126-149">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="f6126-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="f6126-150">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f6126-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="f6126-151">`Main` yönteminizi `WorkingWithStrings` olarak yeniden adlandırın ve `WorkingWithStrings`çağıran yeni bir `Main` yöntemi yazın.</span><span class="sxs-lookup"><span data-stu-id="f6126-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="f6126-152">İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="f6126-152">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="f6126-153">Diğer türlerin listeleri</span><span class="sxs-lookup"><span data-stu-id="f6126-153">Lists of other types</span></span>

<span data-ttu-id="f6126-154">Şu ana kadar listelerde `string` türü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f6126-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="f6126-155"><xref:System.Collections.Generic.List%601> farklı bir tür kullanalım.</span><span class="sxs-lookup"><span data-stu-id="f6126-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="f6126-156">Bir sayı kümesi oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="f6126-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="f6126-157">Aşağıdakileri yeni `Main` yönteminizin altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="f6126-158">Bu, tamsayıların bir listesini oluşturur ve ilk iki tamsayının değerini 1 değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f6126-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="f6126-159">Bunlar bir *Fibonaccı sırasının*ilk iki değeri, bir dizi sayı.</span><span class="sxs-lookup"><span data-stu-id="f6126-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="f6126-160">Her bir sonraki Fibonaccı numarası, önceki iki sayının toplamı alınarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="f6126-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="f6126-161">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6126-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="f6126-162">Sonuçları görmek için dosyayı kaydedin ve `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="f6126-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="f6126-163">Yalnızca bu bölüme odaklanmak için `WorkingWithStrings();`çağıran kodu açıklama olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="f6126-164">Çağrının önüne şu şekilde iki `/` karakteri koymanız yeterlidir: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="f6126-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="f6126-165">Sına</span><span class="sxs-lookup"><span data-stu-id="f6126-165">Challenge</span></span>

<span data-ttu-id="f6126-166">Bu ve önceki derslerden bazılarını bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="f6126-167">Fibonaccı numaralarına en fazla ne kadar derlediğiniz hakkında ' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="f6126-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="f6126-168">Dizideki ilk 20 sayıyı oluşturmak için kodu yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="f6126-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="f6126-169">(İpucu olarak, 20 fibonaccı numarası 6765 ' dir.)</span><span class="sxs-lookup"><span data-stu-id="f6126-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="f6126-170">Sınama Tamam</span><span class="sxs-lookup"><span data-stu-id="f6126-170">Complete challenge</span></span>

<span data-ttu-id="f6126-171">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)örnek bir çözüm görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="f6126-172">Döngünün her tekrarında, listedeki son iki tamsayının yerine getiriyorsunuz ve bu değeri listeye ekliyor olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f6126-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="f6126-173">Döngü, listeye 20 öğe ekleyinceye kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="f6126-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="f6126-174">Tebrikler, liste öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="f6126-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="f6126-175">Kendi geliştirme ortamınızda [sınıflarla tanışın](introduction-to-classes.md) öğreticisine devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="f6126-176">[Koleksiyonlar](../../../standard/collections/index.md)hakkında [.net Kılavuzu](../../../standard/index.md) konusundaki `List` türüyle çalışma hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="f6126-177">Diğer birçok koleksiyon türünü de öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f6126-177">You'll also learn about many other collection types.</span></span>
