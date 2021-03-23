---
title: Koleksiyonlarla çalışma-C# öğreticisine giriş
description: Bu öğreticide liste koleksiyonunu inceleyerek C# öğrenin.
ms.date: 02/05/2021
ms.openlocfilehash: 0043372aed65fbc720a022a3d8c69abd25ceca0c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876109"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="55901-103">Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin</span><span class="sxs-lookup"><span data-stu-id="55901-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="55901-104">Bu giriş öğreticisi, C# diline ve sınıfının temel bilgilerine bir giriş sağlar <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="55901-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55901-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="55901-105">Prerequisites</span></span>

<span data-ttu-id="55901-106">Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="55901-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="55901-107">Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="55901-108">Mac ve Windows 'da, Visual Studio 2019 ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-108">On Mac and Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="55901-109">Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="55901-109">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="55901-110">Temel liste örneği</span><span class="sxs-lookup"><span data-stu-id="55901-110">A basic list example</span></span>

<span data-ttu-id="55901-111">*List-öğreticisi* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55901-111">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="55901-112">Geçerli dizini oluşturun ve çalıştırın `dotnet new console` .</span><span class="sxs-lookup"><span data-stu-id="55901-112">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="55901-113">*Program. cs* ' yi en sevdiğiniz düzenleyicide açın ve mevcut kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="55901-113">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

var names = new List<string> { "<name>", "Ana", "Felipe" };
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="55901-114">`<name>`Adınızla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55901-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="55901-115">*Program.cs* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="55901-115">Save *Program.cs*.</span></span> <span data-ttu-id="55901-116">`dotnet run`Denemek için konsol pencerenizi yazın.</span><span class="sxs-lookup"><span data-stu-id="55901-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="55901-117">Dizelerin bir listesini oluşturdunuz, bu listeye üç ad eklediniz ve adları tüm büyük harfler halinde yazdırdık.</span><span class="sxs-lookup"><span data-stu-id="55901-117">You've created a list of strings, added three names to that list, and printed the names in all CAPS.</span></span> <span data-ttu-id="55901-118">Önceki öğreticilerde, listede döngü gerçekleştirmek için öğrenmiş olduğunuz kavramları kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="55901-118">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="55901-119">Adları görüntülenecek kod, [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="55901-119">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="55901-120">Bir `string` `$` karakterden önce karakterinden sonra, C# kodunu dize bildirimine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="55901-121">Gerçek dize, bu C# kodunun oluşturduğu değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="55901-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="55901-122">Bu örnekte, yöntemini çağırdığı için, her bir adla ' ı, `{name.ToUpper()}` büyük harflere dönüştürülecek şekilde değiştirir <xref:System.String.ToUpper%2A> .</span><span class="sxs-lookup"><span data-stu-id="55901-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="55901-123">Araştırma devam edelim.</span><span class="sxs-lookup"><span data-stu-id="55901-123">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="55901-124">Liste içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="55901-124">Modify list contents</span></span>

<span data-ttu-id="55901-125">Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="55901-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="55901-126">Bu tür öğe dizilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="55901-126">This type stores sequences of elements.</span></span> <span data-ttu-id="55901-127">Açılı ayraçlar arasındaki öğelerin türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-127">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="55901-128">Bu türün önemli bir yönü <xref:System.Collections.Generic.List%601> büyümenin veya küçülebileceği, öğe eklemenize veya kaldırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="55901-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="55901-129">Programınızın sonuna bu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55901-129">Add this code at the end of your program:</span></span>

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

<span data-ttu-id="55901-130">Listenin sonuna iki ad daha eklediniz.</span><span class="sxs-lookup"><span data-stu-id="55901-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="55901-131">Ayrıca bir tane de kaldırmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="55901-131">You've also removed one as well.</span></span> <span data-ttu-id="55901-132">Dosyayı kaydedin ve `dotnet run` denemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="55901-132">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="55901-133">, <xref:System.Collections.Generic.List%601> Tek tek öğeleri **dizine** göre de başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55901-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="55901-134">Dizini, `[` `]` liste adını izleyen ve belirteçleri arasına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="55901-135">C# ilk dizin için 0 kullanır.</span><span class="sxs-lookup"><span data-stu-id="55901-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="55901-136">Bu kodu, yeni eklediğiniz kodun hemen altına ekleyin ve deneyin:</span><span class="sxs-lookup"><span data-stu-id="55901-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="55901-137">Liste sonunun ötesinde bir dizine erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-137">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="55901-138">Dizinlerin 0 ' dan başlayıp, en büyük geçerli dizinin listedeki öğe sayısından bir daha az olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="55901-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="55901-139">Listenin özelliğini ne kadar süreyle kullandığını kontrol edebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> .</span><span class="sxs-lookup"><span data-stu-id="55901-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="55901-140">Programınızın sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55901-140">Add the following code at the end of your program:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="55901-141">Dosyayı kaydedin ve `dotnet run` sonuçları görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="55901-141">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="55901-142">Arama ve sıralama listeleri</span><span class="sxs-lookup"><span data-stu-id="55901-142">Search and sort lists</span></span>

<span data-ttu-id="55901-143">Örneklerimizde görece küçük listeler kullanılıyor, ancak uygulamalarınız genellikle binlerce numaralandırma olan çok sayıda öğesi olan listeler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="55901-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="55901-144">Bu daha büyük koleksiyonlardaki öğeleri bulmak için listede farklı öğeler için arama yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55901-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="55901-145"><xref:System.Collections.Generic.List%601.IndexOf%2A>Yöntemi bir öğe arar ve öğenin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="55901-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="55901-146">Öğe listede yoksa, `IndexOf` döndürür `-1` .</span><span class="sxs-lookup"><span data-stu-id="55901-146">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="55901-147">Bu kodu programınızın altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55901-147">Add this code to the bottom of your program:</span></span>

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

<span data-ttu-id="55901-148">Listenizdeki öğeler de sıralanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="55901-148">The items in your list can be sorted as well.</span></span> <span data-ttu-id="55901-149"><xref:System.Collections.Generic.List%601.Sort%2A>Yöntemi, listedeki tüm öğeleri normal sıralarına göre sıralar (dizeler için alfabetik olarak).</span><span class="sxs-lookup"><span data-stu-id="55901-149">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="55901-150">Bu kodu programınızın altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55901-150">Add this code to the bottom of your program:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="55901-151">`dotnet run`Bu en son sürümü denemek için dosyayı kaydedin ve yazın.</span><span class="sxs-lookup"><span data-stu-id="55901-151">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="55901-152">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="55901-152">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="55901-153">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="55901-153">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="55901-154">Yazdığınız tüm kodu adlı yeni bir yöntemde yerleştirin `WorkWithStrings()` .</span><span class="sxs-lookup"><span data-stu-id="55901-154">Place all the code you've written in a new method called `WorkWithStrings()`.</span></span> <span data-ttu-id="55901-155">Programınızın en üstünde bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="55901-155">Call that method at the top of your program.</span></span> <span data-ttu-id="55901-156">Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="55901-156">When you finish, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

WorkWithString();

void WorkWithString()
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
```

## <a name="lists-of-other-types"></a><span data-ttu-id="55901-157">Diğer türlerin listeleri</span><span class="sxs-lookup"><span data-stu-id="55901-157">Lists of other types</span></span>

<span data-ttu-id="55901-158">`string`Şu ana kadar listelerdeki türü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="55901-158">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="55901-159"><xref:System.Collections.Generic.List%601>Farklı bir tür kullanalım.</span><span class="sxs-lookup"><span data-stu-id="55901-159">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="55901-160">Bir sayı kümesi oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="55901-160">Let's build a set of numbers.</span></span>

<span data-ttu-id="55901-161">' İ çağırdıktan sonra programınıza aşağıdakileri ekleyin `WorkWithStrings()` :</span><span class="sxs-lookup"><span data-stu-id="55901-161">Add the following to your program after you call `WorkWithStrings()`:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="55901-162">Bu, tamsayıların bir listesini oluşturur ve ilk iki tamsayının değerini 1 değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55901-162">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="55901-163">Bunlar bir *Fibonaccı sırasının* ilk iki değeri, bir dizi sayı.</span><span class="sxs-lookup"><span data-stu-id="55901-163">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="55901-164">Her bir sonraki Fibonaccı numarası, önceki iki sayının toplamı alınarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="55901-164">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="55901-165">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55901-165">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="55901-166">Sonuçları görmek için dosyayı kaydedin ve yazın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="55901-166">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="55901-167">Yalnızca bu bölüme odaklanmak için, çağıran kodu açıklama olarak ayarlayabilirsiniz `WorkingWithStrings();` .</span><span class="sxs-lookup"><span data-stu-id="55901-167">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="55901-168">`/`Çağrının önüne şu şekilde iki karakter koymanız yeterlidir: `// WorkingWithStrings();` .</span><span class="sxs-lookup"><span data-stu-id="55901-168">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="55901-169">Sınama</span><span class="sxs-lookup"><span data-stu-id="55901-169">Challenge</span></span>

<span data-ttu-id="55901-170">Bu ve önceki derslerden bazılarını bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-170">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="55901-171">Fibonaccı numaralarına en fazla ne kadar derlediğiniz hakkında ' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="55901-171">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="55901-172">Dizideki ilk 20 sayıyı oluşturmak için kodu yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="55901-172">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="55901-173">(İpucu olarak, 20 fibonaccı numarası 6765 ' dir.)</span><span class="sxs-lookup"><span data-stu-id="55901-173">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="55901-174">Görevi tamamlama</span><span class="sxs-lookup"><span data-stu-id="55901-174">Complete challenge</span></span>

<span data-ttu-id="55901-175">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/main/csharp/list-quickstart/Program.cs#L8-L16)örnek bir çözüm görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-175">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/main/csharp/list-quickstart/Program.cs#L8-L16).</span></span>

<span data-ttu-id="55901-176">Döngünün her tekrarında, listedeki son iki tamsayının yerine getiriyorsunuz ve bu değeri listeye ekliyor olursunuz.</span><span class="sxs-lookup"><span data-stu-id="55901-176">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="55901-177">Döngü, listeye 20 öğe ekleyinceye kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="55901-177">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="55901-178">Tebrikler, liste öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="55901-178">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="55901-179">Kendi geliştirme ortamınızda [ek](../../tutorials/index.md) öğreticilerle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-179">You can continue with [additional](../../tutorials/index.md) tutorials in your own development environment.</span></span>

<span data-ttu-id="55901-180">`List` [Koleksiyonlar](../../../standard/collections/index.md)üzerinde .net temelleri makalesindeki türle çalışma hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-180">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="55901-181">Diğer birçok koleksiyon türünü de öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="55901-181">You'll also learn about many other collection types.</span></span>
