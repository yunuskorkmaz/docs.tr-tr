---
title: Dize ilişkilendirme - C#
description: C# 6'dizesi ilişkilendirme nasıl çalıştığını öğrenin
keywords: .NET, .NET core, C#, dize
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: a9578d006861b987871071961437345c378a5b58
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="85e89-104">C# dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="85e89-104">String Interpolation in C#</span></span> #

<span data-ttu-id="85e89-105">Dize ilişkilendirme bir dize yer tutucuları bir dize değişkeni değeriyle değiştirilir yoludur.</span><span class="sxs-lookup"><span data-stu-id="85e89-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="85e89-106">Bunu yapmanın yolu olan C# 6'dan önce <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85e89-106">Before C# 6, the way to do this is with <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="85e89-107">Bu Tamam çalışır, ancak numaralı yer tutucuları kullandığından, okumak daha zor ve daha ayrıntılı olabilir.</span><span class="sxs-lookup"><span data-stu-id="85e89-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="85e89-108">Diğer programlama dilleri dize ilişkilendirme dilinde yerleşik bir süre beklendiğinden.</span><span class="sxs-lookup"><span data-stu-id="85e89-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="85e89-109">Örneğin, PHP ile:</span><span class="sxs-lookup"><span data-stu-id="85e89-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="85e89-110">C# 6'da, son olarak bu dize ilişkilendirme stilini sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="85e89-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="85e89-111">Kullanabileceğiniz bir `$` önce değişkenleri/ifadeleri değerlerine için alternatif belirtmek için bir dize.</span><span class="sxs-lookup"><span data-stu-id="85e89-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85e89-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="85e89-112">Prerequisites</span></span>
<span data-ttu-id="85e89-113">.NET core çalışmasına, makine ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="85e89-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="85e89-114">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="85e89-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="85e89-115">Bu uygulama, Windows, Ubuntu Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85e89-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="85e89-116">Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85e89-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="85e89-117">Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu.</span><span class="sxs-lookup"><span data-stu-id="85e89-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="85e89-118">Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85e89-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="85e89-119">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="85e89-119">Create the Application</span></span>

<span data-ttu-id="85e89-120">Tüm Araçlar yüklediniz, yeni bir .NET Core uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85e89-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="85e89-121">Komut satırı Oluşturucu kullanmak için projeniz için bir dizin gibi oluşturun `interpolated`ve sık kullanılan kabuğuna şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="85e89-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="85e89-122">Bu komut, bir proje dosyası ile bir temel .NET Core projesi oluşturur *interpolated.csproj*ve kaynak kodu dosyasının *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="85e89-122">This command creates a barebones .NET Core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="85e89-123">Yürütme gerekecek `dotnet restore` bu projeyi derlemek için gerekli bağımlılıkların geri yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="85e89-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="85e89-124">Programı çalıştırmak üzere kullanmadan `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="85e89-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="85e89-125">"Hello, World" çıkışı konsola görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85e89-125">You should see "Hello, World" output to the console.</span></span>



## <a name="intro-to-string-interpolation"></a><span data-ttu-id="85e89-126">İlişkilendirme dize giriş</span><span class="sxs-lookup"><span data-stu-id="85e89-126">Intro to String Interpolation</span></span>

<span data-ttu-id="85e89-127">İle <xref:System.String.Format%2A?displayProperty=nameWithType>, "yer tutucuları" dizesini izleyen bağımsız değişkenleri tarafından değiştirilen bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="85e89-127">With <xref:System.String.Format%2A?displayProperty=nameWithType>, you specify "placeholders" in a string that are replaced by the arguments following the string.</span></span> <span data-ttu-id="85e89-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="85e89-128">For instance:</span></span>

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

<span data-ttu-id="85e89-129">Bu, "adımın Matt Groves olduğu" çıkarır.</span><span class="sxs-lookup"><span data-stu-id="85e89-129">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="85e89-130">C# 6 kullanmak yerine, `String.Format`, Ara değerli bir dize ile başlayan tanımladığınız `$` sembol ve sonra doğrudan dizesindeki değişkenleri kullanma.</span><span class="sxs-lookup"><span data-stu-id="85e89-130">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="85e89-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="85e89-131">For instance:</span></span>

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

<span data-ttu-id="85e89-132">Yalnızca değişkenleri kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="85e89-132">You don't have to use just variables.</span></span> <span data-ttu-id="85e89-133">Köşeli ayraçlar içindeki herhangi bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85e89-133">You can use any expression within the brackets.</span></span> <span data-ttu-id="85e89-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="85e89-134">For instance:</span></span>

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

<span data-ttu-id="85e89-135">Hangi çıktı:</span><span class="sxs-lookup"><span data-stu-id="85e89-135">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="85e89-136">Dize ilişkilendirme nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="85e89-136">How string interpolation works</span></span>

<span data-ttu-id="85e89-137">Arka planda Bu dize ilişkilendirme sözdizimi veri dönüştürülür `String.Format` derleyici tarafından.</span><span class="sxs-lookup"><span data-stu-id="85e89-137">Behind the scenes, this string interpolation syntax is translated into `String.Format` by the compiler.</span></span> <span data-ttu-id="85e89-138">Bu nedenle, yapabileceğiniz [aynı türde öğe işiniz önce ile `String.Format` ](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="85e89-138">So, you can do the [same type of stuff you've done before with `String.Format`](../../standard/base-types/formatting-types.md).</span></span>

<span data-ttu-id="85e89-139">Örneğin, doldurma ve sayısal biçimlendirme ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85e89-139">For instance, you can add padding and numeric formatting:</span></span>

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

<span data-ttu-id="85e89-140">Yukarıdaki gibi bir çıktı:</span><span class="sxs-lookup"><span data-stu-id="85e89-140">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="85e89-141">Bir değişken adı bulunmazsa, derleme zamanı hatası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="85e89-141">If a variable name is not found, then a compile-time error is generated.</span></span>

<span data-ttu-id="85e89-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="85e89-142">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="85e89-143">Bu derleme, hataları alırsınız:</span><span class="sxs-lookup"><span data-stu-id="85e89-143">If you compile this, you get errors:</span></span>
 
* <span data-ttu-id="85e89-144">`Cannot use local variable 'adj' before it is declared` - `adj` değildi değişkeni bildirilen kadar *sonra* Ara değerli dize.</span><span class="sxs-lookup"><span data-stu-id="85e89-144">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="85e89-145">`The name 'otheranimal' does not exist in the current context` -bir değişken adı verilen `otheranimal` hiçbir zaman bile bildirildi</span><span class="sxs-lookup"><span data-stu-id="85e89-145">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="85e89-146">Yerelleştirme ve uluslararası hale getirme</span><span class="sxs-lookup"><span data-stu-id="85e89-146">Localization and Internationalization</span></span>

<span data-ttu-id="85e89-147">Ara değerli bir dize destekleyen <xref:System.IFormattable?displayProperty=nameWithType> ve <xref:System.FormattableString?displayProperty=nameWithType>, hangi uygulamalar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="85e89-147">An interpolated string supports <xref:System.IFormattable?displayProperty=nameWithType> and <xref:System.FormattableString?displayProperty=nameWithType>, which can be useful for internationalization.</span></span>

<span data-ttu-id="85e89-148">Varsayılan olarak, geçerli kültürü Ara değerli bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="85e89-148">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="85e89-149">Farklı bir kültür kullanmak için Ara değerli bir dize olarak cast `IFormattable`.</span><span class="sxs-lookup"><span data-stu-id="85e89-149">To use a different culture, cast an interpolated string as `IFormattable`.</span></span> <span data-ttu-id="85e89-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="85e89-150">For instance:</span></span>

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a><span data-ttu-id="85e89-151">Sonuç</span><span class="sxs-lookup"><span data-stu-id="85e89-151">Conclusion</span></span> 

<span data-ttu-id="85e89-152">Bu öğreticide, dize ilişkilendirme özelliklerinin C# 6'ın nasıl kullanılacağını öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="85e89-152">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="85e89-153">Temel yazma basit daha kısa bir yol olduğu `String.Format` ifadelerle bazı uyarılar için daha gelişmiş kullanır.</span><span class="sxs-lookup"><span data-stu-id="85e89-153">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses.</span></span> <span data-ttu-id="85e89-154">Daha fazla bilgi için bkz: [dize ilişkilendirme](../../csharp//language-reference/tokens/interpolated.md) konu.</span><span class="sxs-lookup"><span data-stu-id="85e89-154">For more information, see the [String interpolation](../../csharp//language-reference/tokens/interpolated.md) topic.</span></span>
