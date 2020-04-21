---
title: String enterpolasyonu - C# öğretici
description: Bu öğretici, daha büyük bir dize biçimlendirilmiş ifade sonuçlarını eklemek için C# dize enterpolasyon özelliğini nasıl kullanacağınızı gösterir.
ms.date: 10/23/2018
ms.openlocfilehash: 22637895f241585bac4909479f225bf3cb581614
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738278"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="e879b-103">Biçimlendirilmiş dizeleri oluşturmak için dize enterpolasyonunu kullanma</span><span class="sxs-lookup"><span data-stu-id="e879b-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="e879b-104">Bu öğretici, değerleri tek bir sonuç dizesine eklemek için C# [dize enterpolasyonunu](../../language-reference/tokens/interpolated.md) nasıl kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="e879b-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="e879b-105">C# kodu yazar sınız ve derleme ve çalıştırma sonuçlarını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e879b-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="e879b-106">Öğretici, değerleri bir dize içine nasıl ekleyip bu değerleri farklı şekillerde biçimlendireceklerini gösteren bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="e879b-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="e879b-107">Bu öğretici, geliştirme için kullanabileceğiniz bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="e879b-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="e879b-108">.NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e879b-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="e879b-109">Ayrıca tarayıcınızda bu öğretici [interaktif sürümünü](interpolated-strings.yml) tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-109">You can also complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="e879b-110">İlişkilendirilmiş dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="e879b-110">Create an interpolated string</span></span>

<span data-ttu-id="e879b-111">*Enterpolasyonadı*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e879b-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="e879b-112">Geçerli dizini yapın ve konsol penceresinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e879b-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="e879b-113">Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e879b-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="e879b-114">En sevdiğiniz düzenleyicide *Program.cs* açın `Console.WriteLine("Hello World!");` ve satırı adınızı değiştirebileceğiniz `<name>` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e879b-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="e879b-115">Konsol pencerenize `dotnet run` yazarak bu kodu deneyin.</span><span class="sxs-lookup"><span data-stu-id="e879b-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="e879b-116">Programı çalıştırdığınızda program, karşılamada adınızı içeren tek bir dize görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e879b-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="e879b-117"><xref:System.Console.WriteLine%2A> Yöntem çağrısında yer alan *dize, enterpolasyonlu dize ifadesidir.*</span><span class="sxs-lookup"><span data-stu-id="e879b-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="e879b-118">Bu, gömülü kod içeren bir dizeden tek bir dize (*sonuç dizesi* olarak adlandırılır) oluşturmanızı sağlayan bir şablon türüdür.</span><span class="sxs-lookup"><span data-stu-id="e879b-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="e879b-119">İlişkilendirilmiş dizeler özellikle bir dizeye değer eklerken veya dizeleri birleştirirken kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="e879b-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="e879b-120">Şu basit örnek her ilişkilendirilmiş dizenin sahip olması gereken iki öğeyi içerir:</span><span class="sxs-lookup"><span data-stu-id="e879b-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="e879b-121">Açma tırnak işareti karakterinden önce `$` karakteriyle başlayan bir dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="e879b-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="e879b-122">`$` sembolü ile tırnak işareti karakteri arasında boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="e879b-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="e879b-123">(Eğer bir tane eklerseniz ne olacağını görmek istiyorsanız, karakterden `$` sonra bir boşluk ekleyin, dosyayı `dotnet run` kaydedin ve konsol penceresine yazarak programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e879b-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="e879b-124">C# derleyicisi bir hata iletisi görüntüler, "hata CS1056: Beklenmeyen karakter '$'".)</span><span class="sxs-lookup"><span data-stu-id="e879b-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="e879b-125">Bir veya daha fazla *enterpolasyon ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="e879b-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="e879b-126">Enterpolasyon ifadesi bir açma ve kapatma`{` `}`ayracı ile gösterilir ( ve).</span><span class="sxs-lookup"><span data-stu-id="e879b-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="e879b-127">Ayraçlar arasında bir değer (`null` dahil) döndüren herhangi bir C# ifadesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="e879b-128">Diğer bazı veri türleri ile birkaç dize enterpolasyon örnekleri deneyelim.</span><span class="sxs-lookup"><span data-stu-id="e879b-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="e879b-129">Farklı veri türleri ekleme</span><span class="sxs-lookup"><span data-stu-id="e879b-129">Include different data types</span></span>

<span data-ttu-id="e879b-130">Önceki bölümde, bir dizeyi diğerinin içine eklemek için dize enterpolasyonunu kullandınız.</span><span class="sxs-lookup"><span data-stu-id="e879b-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="e879b-131">Bir enterpolasyon ifadesinin sonucu olsa da, herhangi bir veri türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e879b-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="e879b-132">Çeşitli veri türlerinin değerlerini enterpolasyonlu bir dizeye ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="e879b-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="e879b-133">Aşağıdaki örnekte, önce bir [özelliği](../../properties.md) `Vegetable` ve `Name` <xref:System.Object.ToString?displayProperty=nameWithType> [yöntemi](../../methods.md)olan `ToString` bir [sınıf](../../programming-guide/classes-and-structs/classes.md) veri türü (yöntemin davranışını [geçersiz kılan)](../../language-reference/keywords/override.md) tanımlarız.</span><span class="sxs-lookup"><span data-stu-id="e879b-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e879b-134">[ `public` Erişim değiştiricisi,](../../language-reference/keywords/public.md) bir örneğin dize gösterimini almak `Vegetable` için bu yöntemi herhangi bir istemci kodu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e879b-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="e879b-135">Örnekte `Vegetable.ToString` `Name` `Vegetable` [yöntem, oluşturucuda](../../programming-guide/classes-and-structs/constructors.md)başharfe dönen özelliğin değerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="e879b-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="e879b-136">Daha sonra [ `new` işleç](../../language-reference/operators/new-operator.md) `Vegetable` kullanarak `item` ve oluşturucu `Vegetable`için bir ad vererek adlı sınıfın bir örneği oluşturmak:</span><span class="sxs-lookup"><span data-stu-id="e879b-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="e879b-137">Son olarak, `item` değişkeni bir <xref:System.DateTime> değer, bir <xref:System.Decimal> değer ve `Unit` [numaralandırma](../../language-reference/builtin-types/enum.md) değeri de içeren enterpolasyonlu bir dizeye dahil ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="e879b-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="e879b-138">Düzenleyicinizdeki C# kodunun tümünün yerine aşağıdaki kodu girin `dotnet run` ve çalıştırmak için komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e879b-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="e879b-139">Enterpolasyon dizesinde enterpolasyon ifadesinin `item` sonuç dizesinde "patlıcan" metnine çözüldüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e879b-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="e879b-140">Bunun nedeni, ifade sonucunun türü bir dize olmadığında, sonucun aşağıdaki şekilde bir dize yle çözülmesidir:</span><span class="sxs-lookup"><span data-stu-id="e879b-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="e879b-141">Enterpolasyon ifadesi , `null`boş bir dize (""veya <xref:System.String.Empty?displayProperty=nameWithType>) için değerlendirilirse.</span><span class="sxs-lookup"><span data-stu-id="e879b-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="e879b-142">Enterpolasyon ifadesi ,genellikle sonuç `null`türünün `ToString` yöntemi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e879b-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="e879b-143">`Vegetable.ToString` Yöntemin uygulanmasını güncelleştirerek bunu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="e879b-144">Her tür bu yöntemin `ToString` bazı uygulama olduğundan bile yöntemi uygulamak için gerek olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e879b-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="e879b-145">Bunu test etmek için, örnekteki `Vegetable.ToString` yöntemin tanımını yorumla (bunu `//`yapmak için, önüne bir yorum sembolü koyun).</span><span class="sxs-lookup"><span data-stu-id="e879b-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="e879b-146">Çıktıda, "patlıcan" dizesi, <xref:System.Object.ToString?displayProperty=nameWithType> yöntemin varsayılan davranışı olan tam nitelikli tür adı (bu örnekte "Sebze" ile) değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e879b-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e879b-147">Numaralandırma değeri `ToString` için yöntemin varsayılan davranışı, değerin dize temsilini döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="e879b-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="e879b-148">Bu örnekten çıktıda, tarih çok kesindir (patlıcanın fiyatı her saniye değişmez) ve fiyat değeri bir birim para birimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="e879b-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="e879b-149">Sonraki bölümde, ifade sonuçlarının dize gösterimlerinin biçimini denetleyerek bu sorunları nasıl düzelteceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="e879b-150">Enterpolasyon ifadelerinin biçimlendirmesini denetleme</span><span class="sxs-lookup"><span data-stu-id="e879b-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="e879b-151">Önceki bölümde, iki kötü biçimlendirilmiş dizeleri sonuç dizesine eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e879b-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="e879b-152">Biri tarih ve saat değeriydi, bunlardan yalnızca tarih değeri uygundu.</span><span class="sxs-lookup"><span data-stu-id="e879b-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="e879b-153">İkincisi, para birimini göstermeyen bir fiyattı.</span><span class="sxs-lookup"><span data-stu-id="e879b-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="e879b-154">Her iki sorun da kolayca giderilebilir.</span><span class="sxs-lookup"><span data-stu-id="e879b-154">Both issues are easy to address.</span></span> <span data-ttu-id="e879b-155">String enterpolasyonu, belirli türlerin biçimlendirmesini denetleyen *biçim dizeleri* belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e879b-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="e879b-156">Aşağıdaki satırda `Console.WriteLine` gösterildiği gibi tarih ve fiyat ifadeleri için biçim dizeleri eklemek için önceki örnekten çağrıyı değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e879b-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="e879b-157">Bir iki nokta üst üste (":") ve biçim dizesi ile enterpolasyon ifadesini izleyerek bir biçim dizesi belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="e879b-158">“d”, kısa tarih biçimini ifade eden [standart tarih ve saat biçimi dizesidir](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier).</span><span class="sxs-lookup"><span data-stu-id="e879b-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="e879b-159">“C2”, ondalık ayırıcıdan sonra gelen iki basamakla para birimi değeri olarak bir sayıyı ifade eden [standart sayısal biçim dizesidir](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier).</span><span class="sxs-lookup"><span data-stu-id="e879b-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="e879b-160">.NET kitaplıklarında bulunan bir dizi tür, önceden tanımlanmış biçim dizeleri kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="e879b-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="e879b-161">Bunlara tüm sayısal türlerin yanı sıra tarih ve saat türleri de dahildir.</span><span class="sxs-lookup"><span data-stu-id="e879b-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="e879b-162">Biçim dizelerini destekleyen türlerin tam listesi için [.NET’teki Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md) başlıklı makalede bulunan [Biçim Dizeleri ve .NET Sınıfı Kitaplık Türleri](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e879b-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="e879b-163">Metin düzenleyicinizdeki biçim dizelerini değiştirmeyi deneyin ve her değişiklik yaptığınızda, değişikliklerin tarih ve saatin biçimlendirmesini ve sayısal değeri nasıl etkilediğini görmek için programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e879b-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="e879b-164">`{date:d}` içindeki “d”yi “t” olarak (kısa saat biçimini görüntülemek için), “y” olarak (yılı ve ayı görüntülemek için) ve “yyyy” olarak (yılı dört basamaklı sayı olarak görüntülemek için) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e879b-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="e879b-165">`{price:C2}` içindeki “C2”yi “e” olarak (üstel gösterim için) ve “F3” olarak (ondalık ayırıcıdan sonra üç basamak içeren sayısal bir değer için) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e879b-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="e879b-166">Biçimlendirmeyi denetlemeye ek olarak, sonuç dizesinde bulunan biçimlendirilmiş dizelerin alan genişliğini ve hizalanmasını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="e879b-167">Bir sonraki bölümde, bunu nasıl yapacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="e879b-168">Enterpolasyon ifadelerinin alan genişliğini ve hizalanmasını denetleme</span><span class="sxs-lookup"><span data-stu-id="e879b-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="e879b-169">Normalde, bir enterpolasyon ifadesinin sonucu dize biçimlendirilmiş olduğunda, bu dize satır aralığı veya boşluklar izlemeden bir sonuç dizesine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e879b-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="e879b-170">Özellikle bir veri kümesiyle çalışırken, alan genişliğini ve metin hizalamasını denetlenebilmek daha okunabilir bir çıktı üretmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e879b-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="e879b-171">Bunu görmek için, metin düzenleyicinizdeki tüm kodu aşağıdaki kodla değiştirin ve ardından programı yürütmek için yazın: `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="e879b-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="e879b-172">Yazarların adları sol hizalı ve yazdıkları başlıklar sağ hizalı.</span><span class="sxs-lookup"><span data-stu-id="e879b-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="e879b-173">Enterpolasyon ifadesinden sonra virgül (",") ekleyerek ve *minimum* alan genişliğini belirleyerek hizalamayı belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="e879b-174">Belirtilen değer pozitif bir sayıysa, alan doğru hizalanır.</span><span class="sxs-lookup"><span data-stu-id="e879b-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="e879b-175">Negatif bir sayıysa, alan sol hizalıdır.</span><span class="sxs-lookup"><span data-stu-id="e879b-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="e879b-176">Negatif işaretleri `{"Author",-25}` ve `{title.Key,-25}` kodu kaldırmayı deneyin ve aşağıdaki kod gibi örneği yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e879b-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="e879b-177">Bu kez, yazar bilgileri sağ hizalanmış.</span><span class="sxs-lookup"><span data-stu-id="e879b-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="e879b-178">Tek bir enterpolasyon ifadesi için bir hizalama belirtici ve biçim dizesi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e879b-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="e879b-179">Bunu yapmak için önce hizalamayı, ardından bir üst üste ve biçim dizesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e879b-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="e879b-180">Yöntemiçindeki `Main` tüm kodu, tanımlı alan genişliklerine sahip üç biçimlendirilmiş dize görüntüleyen aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e879b-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="e879b-181">Daha sonra komutu girerek programı çalıştırın. `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="e879b-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="e879b-182">Çıktı aşağıdaki gibi bir şey görünüyor:</span><span class="sxs-lookup"><span data-stu-id="e879b-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="e879b-183">Dize enterpolasyon eğitimini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="e879b-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="e879b-184">Daha fazla bilgi için C# öğreticisinde [String enterpolasyon](../../language-reference/tokens/interpolated.md) konusuna ve [String enterpolasyonuna](../../tutorials/string-interpolation.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="e879b-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
