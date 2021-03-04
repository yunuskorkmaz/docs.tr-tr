---
title: Dize ilişkilendirme-C# öğreticisi
description: Bu öğreticide, biçimlendirilen ifade sonuçlarını daha büyük bir dizeye eklemek için C# dize ilişkilendirme özelliğinin nasıl kullanılacağı gösterilmektedir.
ms.date: 10/23/2018
ms.openlocfilehash: a80f6d6b118a9dfc4e9ada2122dfc374a137fb4e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103211"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="66b88-103">Biçimlendirilen dizeler oluşturmak için dize ilişkilendirmeyi kullanın</span><span class="sxs-lookup"><span data-stu-id="66b88-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="66b88-104">Bu öğretici, tek bir sonuç dizesine değer eklemek için C# [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) nasıl kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="66b88-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="66b88-105">C# kodu yazar ve bunu derleyip çalıştırmanın sonuçlarını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="66b88-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="66b88-106">Öğretici, bir dizeye değer ekleme ve bu değerleri farklı şekillerde biçimlendirme işlemlerinin nasıl yapılacağını gösteren bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="66b88-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="66b88-107">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="66b88-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="66b88-108">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="66b88-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="66b88-109">Bu öğreticinin [etkileşimli sürümünü](interpolated-strings.yml) tarayıcınızda de tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-109">You can also complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="66b88-110">İlişkilendirilmiş dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="66b88-110">Create an interpolated string</span></span>

<span data-ttu-id="66b88-111">*Enterpolasyonlu* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="66b88-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="66b88-112">Geçerli dizin yapın ve bir konsol penceresinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66b88-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="66b88-113">Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66b88-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="66b88-114">En sevdiğiniz düzenleyicide *program.cs* açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin, burada `<name>` adınızla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="66b88-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="66b88-115">Konsol pencerenizi yazarak bu kodu deneyin `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="66b88-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="66b88-116">Programı çalıştırdığınızda program, karşılamada adınızı içeren tek bir dize görüntüler.</span><span class="sxs-lookup"><span data-stu-id="66b88-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="66b88-117">Yöntem çağrısına dahil edilen dize, <xref:System.Console.WriteLine%2A> bir *enterpolasyonlu dize ifadesidir*.</span><span class="sxs-lookup"><span data-stu-id="66b88-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="66b88-118">Bu, gömülü kod içeren bir dizeden tek bir dize (*sonuç dizesi* olarak adlandırılır) oluşturmanızı sağlayan bir şablon türüdür.</span><span class="sxs-lookup"><span data-stu-id="66b88-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="66b88-119">İlişkilendirilmiş dizeler özellikle bir dizeye değer eklerken veya dizeleri birleştirirken kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="66b88-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="66b88-120">Şu basit örnek her ilişkilendirilmiş dizenin sahip olması gereken iki öğeyi içerir:</span><span class="sxs-lookup"><span data-stu-id="66b88-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="66b88-121">Açma tırnak işareti karakterinden önce `$` karakteriyle başlayan bir dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="66b88-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="66b88-122">`$` sembolü ile tırnak işareti karakteri arasında boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="66b88-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="66b88-123">(Bir tane eklerseniz ne olacağını görmek isterseniz, karakterden sonra bir boşluk ekleyin `$` , dosyayı kaydedin ve konsol penceresine yazarak programı yeniden çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="66b88-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="66b88-124">C# derleyicisi bir hata iletisi görüntülüyor, "Error CS1056: beklenmeyen karakter ' $ '".)</span><span class="sxs-lookup"><span data-stu-id="66b88-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="66b88-125">Bir veya daha fazla *ilişkilendirme ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="66b88-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="66b88-126">Enterpolasyon ifadesi bir açma ve kapatma ayracı (ve) ile belirtilir `{` `}` .</span><span class="sxs-lookup"><span data-stu-id="66b88-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="66b88-127">Ayraçlar arasında bir değer (`null` dahil) döndüren herhangi bir C# ifadesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="66b88-128">Biraz daha farklı veri türleriyle daha fazla dize ilişkilendirme örneği deneyelim.</span><span class="sxs-lookup"><span data-stu-id="66b88-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="66b88-129">Farklı veri türleri ekleme</span><span class="sxs-lookup"><span data-stu-id="66b88-129">Include different data types</span></span>

<span data-ttu-id="66b88-130">Önceki bölümde, bir dizeyi diğerinin içine eklemek için dize ilişkilendirmeyi kullandınız.</span><span class="sxs-lookup"><span data-stu-id="66b88-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="66b88-131">Enterpolasyon ifadesinin sonucu herhangi bir veri türünde olabilir, ancak.</span><span class="sxs-lookup"><span data-stu-id="66b88-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="66b88-132">Enterpolasyonlu bir dizedeki çeşitli veri türlerinin değerlerini ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="66b88-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="66b88-133">Aşağıdaki örnekte, ilk olarak bir özelliği ve yöntemi olan bir [sınıf](../../programming-guide/classes-and-structs/classes.md) veri türü tanımladık `Vegetable` `Name` [](../../properties.md) `ToString` [](../../methods.md), bu, yönteminin davranışını [geçersiz kılar](../../language-reference/keywords/override.md) <xref:System.Object.ToString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66b88-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66b88-134">[ `public` Erişim değiştiricisi](../../language-reference/keywords/public.md) , bu yöntemi bir örneğin dize gösterimini almak için herhangi bir istemci kodu için kullanılabilir hale getirir `Vegetable` .</span><span class="sxs-lookup"><span data-stu-id="66b88-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="66b88-135">Örnekte, `Vegetable.ToString` yöntemi `Name` oluşturucuda başlatılan özelliğin değerini döndürür `Vegetable` [](../../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="66b88-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="66b88-136">Ardından `Vegetable` işlecini kullanarak adlı sınıfının bir örneğini oluşturur `item` ve Oluşturucu için bir [ `new` ](../../language-reference/operators/new-operator.md) ad sağlar `Vegetable` :</span><span class="sxs-lookup"><span data-stu-id="66b88-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="66b88-137">Son olarak, `item` değişkeni de bir <xref:System.DateTime> değer, <xref:System.Decimal> değer ve bir `Unit` [numaralandırma](../../language-reference/builtin-types/enum.md) değeri içeren bir enterpolasyonlu dizeye dahil ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="66b88-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="66b88-138">Düzenleyicinizdeki tüm C# kodunu aşağıdaki kodla değiştirin ve sonra `dotnet run` çalıştırmak için komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="66b88-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;

   public string Name { get; }

   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

<span data-ttu-id="66b88-139">`item`Enterpolasyonlu dizedeki enterpolasyon ifadesinin sonuç dizesinde "eggbitki" metnine çözümlendiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66b88-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="66b88-140">Yani, ifade sonucunun türü bir dize olmadığında, sonuç aşağıdaki şekilde bir dizeye çözülür:</span><span class="sxs-lookup"><span data-stu-id="66b88-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="66b88-141">Enterpolasyon ifadesi olarak değerlendirilirse `null` , boş bir dize ("" veya <xref:System.String.Empty?displayProperty=nameWithType> ) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66b88-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="66b88-142">İlişkilendirme ifadesi olarak değerlendirilmiyorsa `null` , genellikle `ToString` sonuç türünün yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="66b88-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="66b88-143">Yöntemi uygulamasını güncelleştirerek bunu test edebilirsiniz `Vegetable.ToString` .</span><span class="sxs-lookup"><span data-stu-id="66b88-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="66b88-144">`ToString`Her tür bu yöntemin bir uygulamasını kullandığından yöntemi uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="66b88-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="66b88-145">Bunu test etmek için `Vegetable.ToString` örnekteki yöntemin tanımını (bunu yapmak için, önüne bir açıklama simgesi koyun) yorum yapın `//` .</span><span class="sxs-lookup"><span data-stu-id="66b88-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="66b88-146">Çıktıda, "eggbitki" dizesinin yerine, yöntemin varsayılan davranışı olan tam nitelikli tür adı (Bu örnekteki "Vegetable") bulunur <xref:System.Object.ToString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66b88-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66b88-147">`ToString`Bir numaralandırma değeri için yönteminin varsayılan davranışı değerin dize gösterimini döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="66b88-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="66b88-148">Bu örnekteki çıktıda, tarih çok kesin (eggbitki fiyatı her saniye değişmez) ve fiyat değeri bir para birimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="66b88-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="66b88-149">Sonraki bölümde, ifade sonuçlarının dize temsillerini biçimini denetleyerek bu sorunları nasıl düzelteceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="66b88-150">Enterpolasyon ifadelerinin biçimlendirmesini denetleme</span><span class="sxs-lookup"><span data-stu-id="66b88-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="66b88-151">Önceki bölümde, sonuç dizesine hatalı biçimli iki dize eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66b88-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="66b88-152">Biri tarih ve saat değeriydi, bunlardan yalnızca tarih değeri uygundu.</span><span class="sxs-lookup"><span data-stu-id="66b88-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="66b88-153">İkincisi, para birimi birimini göstermediğiniz bir fiyattır.</span><span class="sxs-lookup"><span data-stu-id="66b88-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="66b88-154">Her iki sorun da kolayca giderilebilir.</span><span class="sxs-lookup"><span data-stu-id="66b88-154">Both issues are easy to address.</span></span> <span data-ttu-id="66b88-155">Dize ilişkilendirme, belirli türlerin biçimlendirilmesini denetleyen *Biçim dizelerini* belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66b88-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="66b88-156">`Console.WriteLine`Aşağıdaki satırda gösterildiği gibi, tarih ve fiyat ifadelerine yönelik biçim dizelerini dahil etmek için önceki örnekteki çağrısını değiştirin:</span><span class="sxs-lookup"><span data-stu-id="66b88-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="66b88-157">Bir biçim dizesini, iki nokta üst üste (":") ve biçim dizesiyle birlikte enterpolasyon ifadesini izleyerek belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="66b88-158">“d”, kısa tarih biçimini ifade eden [standart tarih ve saat biçimi dizesidir](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier).</span><span class="sxs-lookup"><span data-stu-id="66b88-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="66b88-159">“C2”, ondalık ayırıcıdan sonra gelen iki basamakla para birimi değeri olarak bir sayıyı ifade eden [standart sayısal biçim dizesidir](../../../standard/base-types/standard-numeric-format-strings.md#currency-format-specifier-c).</span><span class="sxs-lookup"><span data-stu-id="66b88-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#currency-format-specifier-c) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="66b88-160">.NET kitaplıklarında bulunan birçok tür, önceden tanımlanmış bir biçim dizeleri kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="66b88-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="66b88-161">Bunlara tüm sayısal türlerin yanı sıra tarih ve saat türleri de dahildir.</span><span class="sxs-lookup"><span data-stu-id="66b88-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="66b88-162">Biçim dizelerini destekleyen türlerin tam listesi için [.NET’teki Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md) başlıklı makalede bulunan [Biçim Dizeleri ve .NET Sınıfı Kitaplık Türleri](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66b88-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="66b88-163">Metin düzenleyicinizdeki biçim dizelerini değiştirmeyi deneyin ve her değişiklik yaptığınızda, değişikliklerin tarih ve saat ve sayısal değer biçimlendirmesini nasıl etkilediğini görmek için programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66b88-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="66b88-164">`{date:d}` içindeki “d”yi “t” olarak (kısa saat biçimini görüntülemek için), “y” olarak (yılı ve ayı görüntülemek için) ve “yyyy” olarak (yılı dört basamaklı sayı olarak görüntülemek için) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="66b88-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="66b88-165">`{price:C2}` içindeki “C2”yi “e” olarak (üstel gösterim için) ve “F3” olarak (ondalık ayırıcıdan sonra üç basamak içeren sayısal bir değer için) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="66b88-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="66b88-166">Biçimlendirmeyi denetlemenin yanı sıra, sonuç dizesinde bulunan biçimlendirilmiş dizelerin alan genişliğini ve hizalamasını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="66b88-167">Sonraki bölümde bunu nasıl yapacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="66b88-168">Enterpolasyon ifadelerinin alan genişliğini ve hizalamasını denetleme</span><span class="sxs-lookup"><span data-stu-id="66b88-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="66b88-169">Genellikle, bir enterpolasyon ifadesinin sonucu dize olarak biçimlendirildiğinde, bu dize öndeki veya sondaki boşluklar olmadan bir sonuç dizesine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="66b88-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="66b88-170">Özellikle bir veri kümesiyle çalışırken, alan genişliğini denetleyebilmekte ve metin hizalaması daha okunabilir bir çıktı oluşturulmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="66b88-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="66b88-171">Bunu görmek için, metin düzenleyicinizdeki tüm kodu aşağıdaki kodla değiştirin ve ardından `dotnet run` programı yürütmek için yazın:</span><span class="sxs-lookup"><span data-stu-id="66b88-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="66b88-172">Yazarların adları sola hizalanır ve yazdığı başlıklar sağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="66b88-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="66b88-173">Bir ilişkilendirme ifadesinden sonra bir virgül (",") ekleyerek ve *en az* alan genişliğini belirterek hizalamayı belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="66b88-174">Belirtilen değer pozitif bir sayıysa, alan sağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="66b88-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="66b88-175">Negatif bir sayı ise, alan sola hizalanır.</span><span class="sxs-lookup"><span data-stu-id="66b88-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="66b88-176">Ve kodundan negatif işaretleri kaldırmayı deneyin `{"Author",-25}` `{title.Key,-25}` ve aşağıdaki kod olduğu gibi örneği yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66b88-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="66b88-177">Bu kez, yazar bilgileri sağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="66b88-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="66b88-178">Tek bir ilişkilendirme ifadesi için bir hizalama belirleyicisi ve biçim dizesi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b88-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="66b88-179">Bunu yapmak için önce hizalamayı, ardından iki nokta üst üste ve biçim dizesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="66b88-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="66b88-180">Yöntemi içindeki tüm kodu, `Main` tanımlı alan genişlikleri olan üç biçimli dizeyi görüntüleyen aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="66b88-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="66b88-181">Ardından, komutunu girerek programı çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="66b88-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="66b88-182">Çıktı aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="66b88-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="66b88-183">Dize ilişkilendirme öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="66b88-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="66b88-184">Daha fazla bilgi için bkz. [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) konusu ve C# öğreticisinde [dize ilişkilendirme](../string-interpolation.md) .</span><span class="sxs-lookup"><span data-stu-id="66b88-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../string-interpolation.md) tutorial.</span></span>
