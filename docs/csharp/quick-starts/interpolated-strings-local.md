---
title: "Ara değerli dizeler Öğreticisi - C# yerel quickstarts"
description: "Ara değerli dizeler hakkında bu quickstart incude büyük bir dizi deyimde sonucu için C# kod yazın."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: b6089b69eb350fce29f86f19f5abeb44acb4b6b4
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="interpolated-strings"></a><span data-ttu-id="ef4be-103">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="ef4be-103">Interpolated strings</span></span>

<span data-ttu-id="ef4be-104">Bu hızlı başlangıç Ara değerli dizeler C# dilinde bir tek çıkışına dizeye değerleri eklemek için nasıl kullanılacağını öğretir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-104">This quickstart teaches you how to use interpolated strings in C# to insert values into a single ouput string.</span></span> <span data-ttu-id="ef4be-105">C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ef4be-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ef4be-106">Hızlı başlangıç değerleri dizeleri eklemek ve bu değerler farklı şekillerde biçimlendirmek dersleri bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-106">The quickstart contains a series of lessons that insert values into strings, and format those values in different ways.</span></span>

<span data-ttu-id="ef4be-107">Bu Hızlı Başlangıç, geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="ef4be-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="ef4be-108">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="ef4be-109">Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="ef4be-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> 

## <a name="create-an-interpolated-string"></a><span data-ttu-id="ef4be-110">Ara değerli bir dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef4be-110">Create an interpolated string</span></span>

<span data-ttu-id="ef4be-111">Adlı bir dizin oluşturun **Ara değerli quickstart**.</span><span class="sxs-lookup"><span data-stu-id="ef4be-111">Create a directory named **interpolated-quickstart**.</span></span> <span data-ttu-id="ef4be-112">Geçerli dizin olun ve bir konsol penceresinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ef4be-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console -n interpolated -o .
```

<span data-ttu-id="ef4be-113">Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef4be-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ef4be-114">Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.WriteLine("Hello World!");` Burada, yerini aşağıdaki kodla `<name>` adıyla:</span><span class="sxs-lookup"><span data-stu-id="ef4be-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
<span data-ttu-id="ef4be-115">Bu kod yazarak deneyin `dotnet run` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="ef4be-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ef4be-116">Programını çalıştırdığınızda, tebrik adınızı içeren tek bir dize görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ef4be-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="ef4be-117">Dahil dize <xref:System.Console.WriteLine%2A> yöntemi çağrısı bir *Ara değerli dize*.</span><span class="sxs-lookup"><span data-stu-id="ef4be-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="ef4be-118">Tek bir dize oluşturmanıza olanak sağlayan şablon türüdür (adlı *neden dize*) bir dizeden katıştırılmış kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="ef4be-119">Ara değerli dizeler değerleri bir dize veya dize (bir araya getirme) birleştirme eklemek için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef4be-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span> 
    
<span data-ttu-id="ef4be-120">Bu basit örnekte, her ara değerli bir dize olmalıdır iki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef4be-120">This simple example contains the two elements that every interpolated string must have:</span></span> 

- <span data-ttu-id="ef4be-121">İle başlayan bir değişmez dize değeri `$` açılış tırnak işaretlemeden önce karakter karakter.</span><span class="sxs-lookup"><span data-stu-id="ef4be-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="ef4be-122">Arasında herhangi bir boşluk olamaz `$` simge ve tırnak işareti karakteri.</span><span class="sxs-lookup"><span data-stu-id="ef4be-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="ef4be-123">(Görmek isterseniz ne olur bir eklerseniz, bir boşluk sonra `$` karakter, dosyayı kaydedin ve yazarak programı yeniden çalıştırın `dotnet run` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="ef4be-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="ef4be-124">C# Derleyici bir hata iletisi görüntüler "hata CS1056: Beklenmeyen karakter '$'".)</span><span class="sxs-lookup"><span data-stu-id="ef4be-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span> 

- <span data-ttu-id="ef4be-125">Bir veya daha fazla *Ara değerli ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="ef4be-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="ef4be-126">Ara değerli bir ifadenin bir açma ve kapatma parantezi tarafından belirtilir (`{` ve `}`).</span><span class="sxs-lookup"><span data-stu-id="ef4be-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="ef4be-127">Bir değer döndürür herhangi C# ifade koyabilirsiniz (de dahil olmak üzere `null`) kaşlı ayraçlar içinde.</span><span class="sxs-lookup"><span data-stu-id="ef4be-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span> 

<span data-ttu-id="ef4be-128">Diğer veri türlerine sahip birkaç fazla ara değerli dize örnek deneyelim.</span><span class="sxs-lookup"><span data-stu-id="ef4be-128">Let's try a few more interpolated string examples with some other data types.</span></span>
    
## <a name="include-different-data-types"></a><span data-ttu-id="ef4be-129">Farklı veri türlerini içerir</span><span class="sxs-lookup"><span data-stu-id="ef4be-129">Include different data types</span></span>

<span data-ttu-id="ef4be-130">Önceki bölümde Ara değerli bir dize içinde başka bir dize eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef4be-130">In the previous section, you used an interpolated string to insert one string inside of another.</span></span> <span data-ttu-id="ef4be-131">Ara değerli dize ifadesi ancak herhangi bir veri türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-131">An interpolated string expression can be any data type, though.</span></span> <span data-ttu-id="ef4be-132">Birden çok veri türlerinin değerlerine sahip bir ara değerli dize deneyelim.</span><span class="sxs-lookup"><span data-stu-id="ef4be-132">Let's try an interpolated string that has values of multiple data types.</span></span> 
    
<span data-ttu-id="ef4be-133">Aşağıdaki örnek, Ara değerli ifadelerle içerir bir `Vegetable` nesnesi, bir üyesi `Unit` numaralandırma, bir <xref:System.DateTime> değeri ve <xref:System.Decimal> değeri.</span><span class="sxs-lookup"><span data-stu-id="ef4be-133">The following example includes interpolated expressions with a `Vegetable` object, a member of the `Unit` enumeration, a <xref:System.DateTime> value, and a <xref:System.Decimal> value.</span></span> <span data-ttu-id="ef4be-134">Tüm düzenleyicinizde C# kodu aşağıdaki kodla değiştirin ve sonra `console run` komutu çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="ef4be-134">Replace all of the C# code in your editor with the following code, and then use the `console run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
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
    
<span data-ttu-id="ef4be-135">İkinci ifade Ara değerli Not dahildir `item` nesne konsolda görüntülenen sonuç dizesinde ve bu durumda "eggplant" dizesi sonuç dizesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-135">Note that the second interpolated expression includes the `item` object in the result string that's displayed to the console, and in this case the string "eggplant" is inserted into the result string.</span></span> <span data-ttu-id="ef4be-136">Ara değerli ifade türü bir dize değil, C# Derleyici aşağıdakileri yapar nedeni:</span><span class="sxs-lookup"><span data-stu-id="ef4be-136">That's because, when the type of an interpolated expression is not a string, the C# compiler does the following:</span></span>

- <span data-ttu-id="ef4be-137">Ara değerli ifade ise `null`, Ara değerli ifade boş bir dize döndürür ("", veya <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ef4be-137">If the interpolated expression is `null`, the interpolated expression returns an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>).</span></span>

- <span data-ttu-id="ef4be-138">Ara değerli ifade değilse `null`, `ToString` Ara değerli ifade türü yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ef4be-138">If the interpolated expression is not `null`, the `ToString` method of the type of the interpolated expression is called.</span></span> <span data-ttu-id="ef4be-139">Bu tanımını yorum tarafından test `Vegetable.ToString` açıklama simgesini koyarak örnekte yöntemi (`//`), önünde.</span><span class="sxs-lookup"><span data-stu-id="ef4be-139">You can test this by commenting out the definition of the `Vegetable.ToString` method in the example by putting a comment symbol (`//`) in front of it.</span></span> <span data-ttu-id="ef4be-140">Çıktıda "eggplant" dize türü tarafından değiştirilir adı, "Meyve", varsayılan davranışını olduğu <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef4be-140">In the output, the string "eggplant" is replaced by the type name, "Vegetable", which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span>   

<span data-ttu-id="ef4be-141">Bu örnek çıkışı, tarih (eggplant fiyat ikinciye farklılık göstermez) çok kesin ve Fiyat değerini para birimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="ef4be-141">In the output from this example, the date is too precise (the price of eggplant does not vary by the second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="ef4be-142">Sonraki bölümde, Ara değerli ifadeleri tarafından döndürülen dize biçimi denetleyerek bu sorunları gidermeye yönelik bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ef4be-142">In the next section, you'll learn how to fix those issues by controlling the format of strings returned by interpolated expressions.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="ef4be-143">Ara değerli ifadelerin biçimlendirme denetimi</span><span class="sxs-lookup"><span data-stu-id="ef4be-143">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="ef4be-144">Önceki bölümde, iki hatalı biçimlendirilmiş dizeler sonuç dizeye eklendi.</span><span class="sxs-lookup"><span data-stu-id="ef4be-144">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="ef4be-145">Bir yalnızca tarih uygun bir tarih ve saat değeri idi.</span><span class="sxs-lookup"><span data-stu-id="ef4be-145">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="ef4be-146">İkinci para birimi, birim belirtmeyen bir fiyat oluştu.</span><span class="sxs-lookup"><span data-stu-id="ef4be-146">The second was a price that did not indicate its unit of currency.</span></span> <span data-ttu-id="ef4be-147">Her iki adresine kolay sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="ef4be-147">Both issues are easy to address.</span></span> <span data-ttu-id="ef4be-148">Ara değerli ifadeleri içerebilir *biçim dizeleri* kontrol eden biçimlendirme belirli tür.</span><span class="sxs-lookup"><span data-stu-id="ef4be-148">Interpolated expressions can include *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="ef4be-149">Çağrı değiştirme `Console.WriteLine` önceki örnekten tarih ve fiyat alanları için biçim belirticisi aşağıdaki satırda gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ef4be-149">Modify the call to `Console.WriteLine` from the previous example to include the format specifier for the date and price fields as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
<span data-ttu-id="ef4be-150">Ara değerli ifade bir iki nokta üst üste ve biçim dizesi ile izleyerek bir biçim dizesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="ef4be-150">You specify a format string by following the interpolated expression with a colon and the format string.</span></span> <span data-ttu-id="ef4be-151">"d" bir [standart tarih ve saat biçim dizesi](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) kısa tarih biçiminde temsil eden.</span><span class="sxs-lookup"><span data-stu-id="ef4be-151">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="ef4be-152">"C2" olan bir [standart sayısal biçim dizesi](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) bir sayı olarak iki basamaklı bir para birimi değeri ondalık ayırıcıdan sonra temsil eden.</span><span class="sxs-lookup"><span data-stu-id="ef4be-152">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="ef4be-153">.NET standart kitaplıkları türlerinde bir dizi önceden tanımlanmış bir biçim dizeleri kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="ef4be-153">A number of types in the .NET Standard libraries support a predefined set of format strings.</span></span> <span data-ttu-id="ef4be-154">Bu, tüm sayısal türler ve tarih ve saat türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-154">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="ef4be-155">Biçim dizeleri destekleyen türler tam bir listesi için bkz: [biçim dizeleri ve .NET sınıf kitaplığı türleri](../../standard/base-types/formatting-types.md#stringRef) içinde [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="ef4be-155">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span> <span data-ttu-id="ef4be-156">Herhangi bir tür biçim dizeleri kümesi destekleyebilir ve varolan türleri için özel biçimlendirme sağlayan özel biçimlendirme uzantıları da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef4be-156">Any type can support a set of format strings, and you can also develop custom formatting extensions that provide custom formatting for existing types.</span></span> <span data-ttu-id="ef4be-157">Özel biçimlendirme sağlayarak hakkında bilgi için bir <xref:System.ICustomFormatter> uygulama, bkz: [özel biçimlendirme ICustomFormatter ile](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) içinde [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) makale.</span><span class="sxs-lookup"><span data-stu-id="ef4be-157">For information on custom formatting by providing an <xref:System.ICustomFormatter> implementation, see [Custom Formatting with ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="ef4be-158">Biçim dizeleri, metin düzenleyici ve, tarih ve saat ile sayısal değerin biçimlendirme değişikliklerin nasıl etkilediğini görmek için programı yeniden çalıştırın, bir değişiklik yaptığınızda değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="ef4be-158">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="ef4be-159">"D" değiştirmek `{date:d}` "(kısa saat biçimine görüntülemek için) t", "(yıl ve ay görüntülemek için) y" ve "yyyy" (yılı dört basamaklı bir sayı görüntülemek için).</span><span class="sxs-lookup"><span data-stu-id="ef4be-159">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="ef4be-160">"C2" değiştirmek `{price:C2}` "e" (üstel gösterimde) ve (için ondalık ayırıcıdan sonra üç basamaklı sayısal bir değer) "F3".</span><span class="sxs-lookup"><span data-stu-id="ef4be-160">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="ef4be-161">Biçimlendirme denetleme ek olarak, bir ara değerli ifadesi tarafından döndürülen dize hizalamasını ve alan genişliği de denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef4be-161">In addition to controlling formatting, you can also control the field width and alignment of the strings returned by an interpolated expression.</span></span> <span data-ttu-id="ef4be-162">Sonraki bölümde, bunun nasıl yapılacağı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ef4be-162">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="ef4be-163">Ara değerli ifadeleri hizalamasını ve alan genişliği denetleme</span><span class="sxs-lookup"><span data-stu-id="ef4be-163">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="ef4be-164">Normalde, bir ara değerli ifadesi tarafından döndürülen dize sonuç dizesinde yer aldığında, başında veya sonunda boşluk içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ef4be-164">Ordinarily, when the string returned by an interpolated expression is included in a result string, it has no leading or trailing spaces.</span></span> <span data-ttu-id="ef4be-165">Özellikle, kullanmakta olduğunuz bir veri kümesi, Ara değerli ifadeler ile örneklerini alan genişliği ve onun hizalamasını belirtin olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef4be-165">Particularly for instances in which you are working with a set of data, interpolated expressions let you specify a field width and its alignment.</span></span> <span data-ttu-id="ef4be-166">Bu, bir metin düzenleyicisinde tüm kodu aşağıdaki kodla değiştirin görmek için yazın `console run` programı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="ef4be-166">To see this, replace all the code in your text editor with the following code, then type `console run` to execute the program:</span></span>
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
<span data-ttu-id="ef4be-167">Yazarları adlarının sola hizalı ve bunlar yazdı başlıklarını sağa hizalı.</span><span class="sxs-lookup"><span data-stu-id="ef4be-167">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="ef4be-168">Virgül ekleyerek hizalamasını belirtin (",") ifade ve alan genişliği belirleme sonra.</span><span class="sxs-lookup"><span data-stu-id="ef4be-168">You specify the alignment by adding a comma (",") after the expression and designating the field width.</span></span> <span data-ttu-id="ef4be-169">Alan genişliği pozitif bir sayı ise, sağa hizalı alandır:</span><span class="sxs-lookup"><span data-stu-id="ef4be-169">If the field width is a positive number, the field is right-aligned:</span></span>

```text
{expression, width}
```

<span data-ttu-id="ef4be-170">Alan genişliği negatif bir sayı ise, sola hizalı alandır:</span><span class="sxs-lookup"><span data-stu-id="ef4be-170">If the field width is a negative number, the field is left-aligned:</span></span>

```text
{expression, -width}
```

<span data-ttu-id="ef4be-171">Gelen negatif işaretler kaldırmayı deneyin `{"Author",-25}` ve `{title.Key,-25}` Ara değerli ifadeleri ve aşağıdaki kodu yaptığı gibi örneği yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ef4be-171">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` interpolated expressions and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

<span data-ttu-id="ef4be-172">Bu süre, yazar sağa hizalı bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-172">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="ef4be-173">Bir alan genişliği ve tek bir ara değerli ifadede bir biçim dizesi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef4be-173">You can combine a field width and a format string in a single interpolated expression.</span></span> <span data-ttu-id="ef4be-174">Ardından bir iki nokta üst üste ve biçim dizesi alan genişliği önce gelir.</span><span class="sxs-lookup"><span data-stu-id="ef4be-174">The field width comes first, followed by a colon and the format string.</span></span> <span data-ttu-id="ef4be-175">Tüm içinde kod değiştirmek `Main` üç biçimlendirilmiş dizelerle görüntüleyen yöntemi aşağıdaki kod ile tanımlanan genişlikleriyle.</span><span class="sxs-lookup"><span data-stu-id="ef4be-175">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="ef4be-176">Ardından girerek programı çalıştırın `dotnet run` komutu.</span><span class="sxs-lookup"><span data-stu-id="ef4be-176">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
<span data-ttu-id="ef4be-177">Çıktı aşağıdakine benzer görünür:</span><span class="sxs-lookup"><span data-stu-id="ef4be-177">The output looks something like the following:</span></span>

```console
1/11/2018            Hour 09                1,063.34 feet
```

<span data-ttu-id="ef4be-178">Ara değerli dizeler hızlı başlangıç tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="ef4be-178">You've completed the interpolated strings quickstart.</span></span> 
    
<span data-ttu-id="ef4be-179">İle devam edebilirsiniz [dizileri ve koleksiyonları](arrays-and-collections.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="ef4be-179">You can continue with the [Arrays and collections](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="ef4be-180">Ara değerli dizeler ile çalışma hakkında daha fazla bilgiyi [Ara değerli dizeler](../language-reference/keywords/interpolated-strings.md) C# Başvurusu'nda başlığı.</span><span class="sxs-lookup"><span data-stu-id="ef4be-180">You can learn more about working with interpolated strings in the [Interpolated Strings](../language-reference/keywords/interpolated-strings.md) topic in the C# Reference.</span></span>

