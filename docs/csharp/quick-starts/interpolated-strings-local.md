---
title: İlişkilendirme Öğreticisi - C# yerel quickstarts dize
description: Bu Hızlı Başlangıç, C# dize ilişkilendirme özelliği daha büyük bir dize biçimlendirilmiş ifade sonuçlarında için nasıl kullanılacağını gösterir.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: a4e8434b3e7f945ad002984ad7861c0e103c0cf2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="string-interpolation"></a><span data-ttu-id="b52a3-103">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="b52a3-103">String interpolation</span></span>

<span data-ttu-id="b52a3-104">Bu hızlı başlangıç C# kullanmayı öğretir [dize ilişkilendirme](../language-reference/tokens/interpolated.md) tek bir sonuç dizeye değerleri eklemek için.</span><span class="sxs-lookup"><span data-stu-id="b52a3-104">This quickstart teaches you how to use C# [string interpolation](../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="b52a3-105">C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b52a3-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="b52a3-106">Hızlı başlangıç değerleri bir dize olarak ekleyin ve bu değerler farklı şekillerde biçimlendirmek nasıl Göster dersleri bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-106">The quickstart contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="b52a3-107">Bu Hızlı Başlangıç, geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="b52a3-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="b52a3-108">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="b52a3-109">Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="b52a3-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> <span data-ttu-id="b52a3-110">Aynı zamanda gerçekleştirebileceğinizi [etkileşimli sürüm](interpolated-strings.yml) tarayıcınızda Bu hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="b52a3-110">You also can complete the [interactive version](interpolated-strings.yml) of this quickstart in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="b52a3-111">Ara değerli bir dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="b52a3-111">Create an interpolated string</span></span>

<span data-ttu-id="b52a3-112">Adlı bir dizin oluşturun **Ara değerli**.</span><span class="sxs-lookup"><span data-stu-id="b52a3-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="b52a3-113">Geçerli dizin olun ve bir konsol penceresinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b52a3-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="b52a3-114">Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b52a3-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="b52a3-115">Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.WriteLine("Hello World!");` Burada, yerini aşağıdaki kodla `<name>` adıyla:</span><span class="sxs-lookup"><span data-stu-id="b52a3-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="b52a3-116">Bu kod yazarak deneyin `dotnet run` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="b52a3-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="b52a3-117">Programını çalıştırdığınızda, tebrik adınızı içeren tek bir dize görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b52a3-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="b52a3-118">Dahil dize <xref:System.Console.WriteLine%2A> yöntemi çağrısı bir *Ara değerli dize*.</span><span class="sxs-lookup"><span data-stu-id="b52a3-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="b52a3-119">Tek bir dize oluşturmanıza olanak sağlayan şablon türüdür (adlı *neden dize*) bir dizeden katıştırılmış kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="b52a3-120">Ara değerli dizeler değerleri bir dize veya dize (bir araya getirme) birleştirme eklemek için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="b52a3-121">Bu basit örnekte, her ara değerli bir dize olmalıdır iki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b52a3-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="b52a3-122">İle başlayan bir değişmez dize değeri `$` açılış tırnak işaretlemeden önce karakter karakter.</span><span class="sxs-lookup"><span data-stu-id="b52a3-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="b52a3-123">Arasında herhangi bir boşluk olamaz `$` simge ve tırnak işareti karakteri.</span><span class="sxs-lookup"><span data-stu-id="b52a3-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="b52a3-124">(Görmek isterseniz ne olur bir eklerseniz, bir boşluk sonra `$` karakter, dosyayı kaydedin ve yazarak programı yeniden çalıştırın `dotnet run` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="b52a3-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="b52a3-125">C# Derleyici bir hata iletisi görüntüler "hata CS1056: Beklenmeyen karakter '$'".)</span><span class="sxs-lookup"><span data-stu-id="b52a3-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="b52a3-126">Bir veya daha fazla *Ara değerli ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="b52a3-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="b52a3-127">Ara değerli bir ifadenin bir açma ve kapatma parantezi tarafından belirtilir (`{` ve `}`).</span><span class="sxs-lookup"><span data-stu-id="b52a3-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="b52a3-128">Bir değer döndürür herhangi C# ifade koyabilirsiniz (de dahil olmak üzere `null`) kaşlı ayraçlar içinde.</span><span class="sxs-lookup"><span data-stu-id="b52a3-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="b52a3-129">Diğer veri türlerine sahip birkaç daha fazla dize ilişkilendirme örnek deneyelim.</span><span class="sxs-lookup"><span data-stu-id="b52a3-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="b52a3-130">Farklı veri türlerini içerir</span><span class="sxs-lookup"><span data-stu-id="b52a3-130">Include different data types</span></span>

<span data-ttu-id="b52a3-131">Önceki bölümde dize ilişkilendirme içinde başka bir dize eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="b52a3-132">Ara değerli ifade sonucu herhangi bir veri türü yine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="b52a3-133">Şimdi Ara değerli bir dize çeşitli veri türlerinin değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="b52a3-134">Aşağıdaki örnekte, ilk olarak, tanımlarız bir [sınıfı](../programming-guide/classes-and-structs/classes.md) veri türü `Vegetable` olan `Name` [özelliği](../properties.md) ve `ToString` [yöntemi](../methods.md), hangi [geçersiz kılmaları](../language-reference/keywords/override.md) davranışını <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-134">In the following example, first, we define a [class](../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has the `Name` [property](../properties.md) and the `ToString` [method](../methods.md), which [overrides](../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b52a3-135">[ `public` Erişim değiştiricisi](../language-reference/keywords/public.md) bu yöntem dize gösterimini almak için herhangi bir istemci kod için kullanılabilir hale getirir bir `Vegetable` örneği.</span><span class="sxs-lookup"><span data-stu-id="b52a3-135">The [`public` access modifier](../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="b52a3-136">Örnekte `Vegetable.ToString` yöntemi değerini döndürür `Name` konumunda başlatılan özelliği `Vegetable` [Oluşturucusu](../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="b52a3-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="b52a3-137">Biz örneği oluşturup `Vegetable` kullanarak sınıfı [ `new` anahtar sözcüğü](../language-reference/keywords/new-operator.md) ve Oluşturucusu name parametresi sağlanarak `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="b52a3-137">Then we create an instance of the `Vegetable` class by using [`new` keyword](../language-reference/keywords/new-operator.md) and providing a name parameter for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="b52a3-138">Son olarak, eklediğimiz `item` de içeren bir ara değerli dizesine değişken bir <xref:System.DateTime> değeri, bir <xref:System.Decimal> değeri ve `Unit` [numaralandırması](../programming-guide/enumeration-types.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="b52a3-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="b52a3-139">Tüm düzenleyicinizde C# kodu aşağıdaki kodla değiştirin ve sonra `dotnet run` komutu çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="b52a3-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="b52a3-140">Unutmayın Ara değerli ifade `item` Ara değerli dizesinde çözümler sonuç dizesinde "eggplant" metin.</span><span class="sxs-lookup"><span data-stu-id="b52a3-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="b52a3-141">İfade sonucunun türü dize olmadığı durumlarda, sonuç aşağıdaki biçimde bir dizeye çözülmüş nedeni:</span><span class="sxs-lookup"><span data-stu-id="b52a3-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="b52a3-142">Ara değerli ifade değerlendirilirse `null`, boş bir dize ("", veya <xref:System.String.Empty?displayProperty=nameWithType>) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="b52a3-143">Ara değerli ifadesini değerlendiremedi değil, `null`, genellikle `ToString` sonuç türü yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="b52a3-144">Bu uygulanması güncelleştirerek test `Vegetable.ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="b52a3-145">Hatta değil uygulayabilir `ToString` her C# veri türü bu yöntem bazı uygulaması olduğundan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-145">You might even not implement `ToString` method since every C# data type has some implementation of this method.</span></span> <span data-ttu-id="b52a3-146">Test için açıklama tanımı `Vegetable.ToString` örnekte yöntemi (Bunu yapmak için bir açıklama simgesini put `//` önüne).</span><span class="sxs-lookup"><span data-stu-id="b52a3-146">To test that, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol `//` in front of it).</span></span> <span data-ttu-id="b52a3-147">Çıktıda varsayılan davranışı olan tam olarak nitelenmiş tür adıyla ("Vegetable" Bu örnekte), "eggplant" dizesi değiştirilir, <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b52a3-148">Varsayılan davranışını `ToString` bir numaralandırma türü için yöntemidir numaralandırma tanımı sırasında kullanılan bir değeri dize gösterimini dönün.</span><span class="sxs-lookup"><span data-stu-id="b52a3-148">Default behavior of the `ToString` method for an enumeration type is to return the string representation of a value used at the definition of the enumeration.</span></span>

<span data-ttu-id="b52a3-149">Bu örnek çıkışı, tarih (eggplant fiyat saniyede değiştirmez) çok kesin ve Fiyat değerini para birimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="b52a3-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="b52a3-150">Sonraki bölümde, dize ifadesi sonuçları gösterimlerini biçimini kontrol ederek bu sorunları gidermeye yönelik bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b52a3-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="b52a3-151">Ara değerli ifadelerin biçimlendirme denetimi</span><span class="sxs-lookup"><span data-stu-id="b52a3-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="b52a3-152">Önceki bölümde, iki hatalı biçimlendirilmiş dizeler sonuç dizeye eklendi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="b52a3-153">Bir yalnızca tarih uygun bir tarih ve saat değeri idi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="b52a3-154">İkinci para birimi, birim belirtmek istemediğiniz bir fiyat oluştu.</span><span class="sxs-lookup"><span data-stu-id="b52a3-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="b52a3-155">Her iki adresine kolay sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-155">Both issues are easy to address.</span></span> <span data-ttu-id="b52a3-156">Dize ilişkilendirme belirtmenize olanak sağlar *biçim dizeleri* kontrol eden biçimlendirme belirli tür.</span><span class="sxs-lookup"><span data-stu-id="b52a3-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="b52a3-157">Çağrı değiştirme `Console.WriteLine` önceki örnekten tarih ve fiyat ifadeler için biçim dizeleri aşağıdaki satırda gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b52a3-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="b52a3-158">Ara değerli ifadesi iki nokta ile izleyerek bir biçim dizesi belirtin (":") ve biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="b52a3-159">"d" bir [standart tarih ve saat biçim dizesi](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) kısa tarih biçiminde temsil eden.</span><span class="sxs-lookup"><span data-stu-id="b52a3-159">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="b52a3-160">"C2" olan bir [standart sayısal biçim dizesi](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) bir sayı olarak iki basamaklı bir para birimi değeri ondalık ayırıcıdan sonra temsil eden.</span><span class="sxs-lookup"><span data-stu-id="b52a3-160">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="b52a3-161">.NET kitaplıklarına türlerinde bir dizi önceden tanımlanmış bir biçim dizeleri kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="b52a3-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="b52a3-162">Bu, tüm sayısal türler ve tarih ve saat türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="b52a3-163">Biçim dizeleri destekleyen türler tam bir listesi için bkz: [biçim dizeleri ve .NET sınıf kitaplığı türleri](../../standard/base-types/formatting-types.md#stringRef) içinde [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="b52a3-164">Biçim dizeleri, metin düzenleyici ve, tarih ve saat ile sayısal değerin biçimlendirme değişikliklerin nasıl etkilediğini görmek için programı yeniden çalıştırın, bir değişiklik yaptığınızda değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="b52a3-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="b52a3-165">"D" değiştirmek `{date:d}` "(kısa saat biçimine görüntülemek için) t", "(yıl ve ay görüntülemek için) y" ve "yyyy" (yılı dört basamaklı bir sayı görüntülemek için).</span><span class="sxs-lookup"><span data-stu-id="b52a3-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="b52a3-166">"C2" değiştirmek `{price:C2}` "e" (üstel gösterimde) ve (için ondalık ayırıcıdan sonra üç basamaklı sayısal bir değer) "F3".</span><span class="sxs-lookup"><span data-stu-id="b52a3-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="b52a3-167">Biçimlendirme denetleme ek olarak sonuç dizesinde bulunan biçimlendirilmiş dizeler hizalamasını ve alan genişliği de denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b52a3-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="b52a3-168">Sonraki bölümde, bunun nasıl yapılacağı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b52a3-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="b52a3-169">Ara değerli ifadeleri hizalamasını ve alan genişliği denetleme</span><span class="sxs-lookup"><span data-stu-id="b52a3-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="b52a3-170">Ara değerli bir ifadenin sonucu dize olarak biçimlendirildiğinde normalde, bu dize bir sonuç dizesinde başında veya sonunda boşluk dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="b52a3-171">Özellikle, bir veri kümesiyle bir alan genişliği denetim sahibi çalışırken ve metin hizalamasını daha okunabilir bir çıktı oluşturmak için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b52a3-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="b52a3-172">Bu, bir metin düzenleyicisinde tüm kodu aşağıdaki kodla değiştirin görmek için yazın `dotnet run` programı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="b52a3-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="b52a3-173">Yazarları adlarının sola hizalı ve bunlar yazdı başlıklarını sağa hizalı.</span><span class="sxs-lookup"><span data-stu-id="b52a3-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="b52a3-174">Virgül ekleyerek hizalamasını belirtin (",") Ara değerli bir ifade sonra ve belirleme *minimum* alan genişliği.</span><span class="sxs-lookup"><span data-stu-id="b52a3-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="b52a3-175">Belirtilen değer pozitif bir sayı ise, sağa hizalı alanıdır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="b52a3-176">Negatif bir sayı ise, sola hizalı alanıdır.</span><span class="sxs-lookup"><span data-stu-id="b52a3-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="b52a3-177">Gelen negatif işaretler kaldırmayı deneyin `{"Author",-25}` ve `{title.Key,-25}` kod ve aşağıdaki kodu yaptığı gibi örneği yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b52a3-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="b52a3-178">Bu süre, yazar sağa hizalı bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="b52a3-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="b52a3-179">Hizalama belirticisi ve tek bir ara değerli ifade için bir biçim dizesi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b52a3-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="b52a3-180">Bunu yapmak için ardından iki nokta ve biçim dizesi hizalama önce belirtin.</span><span class="sxs-lookup"><span data-stu-id="b52a3-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="b52a3-181">Tüm içinde kod değiştirmek `Main` üç biçimlendirilmiş dizelerle görüntüleyen yöntemi aşağıdaki kod ile tanımlanan genişlikleriyle.</span><span class="sxs-lookup"><span data-stu-id="b52a3-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="b52a3-182">Ardından girerek programı çalıştırın `dotnet run` komutu.</span><span class="sxs-lookup"><span data-stu-id="b52a3-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="b52a3-183">Çıktı aşağıdakine benzer görünür:</span><span class="sxs-lookup"><span data-stu-id="b52a3-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="b52a3-184">Dize ilişkilendirme quickstart tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="b52a3-184">You've completed the string interpolation quickstart.</span></span>

<span data-ttu-id="b52a3-185">İle devam edebilirsiniz [listesinde koleksiyonu](arrays-and-collections.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="b52a3-185">You can continue with the [List collection](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="b52a3-186">Daha fazla bilgi için bkz: [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu ve [dize ilişkilendirme C#](../tutorials/string-interpolation.md) Öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="b52a3-186">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>
