---
description: Koşullu derlemeyi, uyarıları, null yapılabilir analizini ve daha fazlasını denetleyen farklı C# önişlemci yönergelerini öğrenin
title: C# ön işlemci yönergeleri
ms.date: 03/17/2021
f1_keywords:
- cs.preprocessor
- '#nullable'
- '#if'
- '#else'
- '#elif'
- '#endif'
- '#define'
- '#undef'
- '#warning'
- '#error'
- '#line'
- '#region'
- '#endregion'
- '#pragma'
- '#pragma warning'
- '#pragma checksum'
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
- '#nullable directive [C#]'
- '#if directive [C#]'
- '#else directive [C#]'
- '#elif directive [C#]'
- '#endif directive [C#]'
- '#define directive [C#]'
- '#undef directive [C#]'
- '#warning directive [C#]'
- '#error directive [C#]'
- '#line directive [C#]'
- '#region directive [C#]'
- '#endregion directive [C#]'
- '#pragma directive [C#]'
- '#pragma warning [C#]'
- '#pragma checksum [C#]'
ms.openlocfilehash: 373952282a684da25414af9853e18b7bc4874108
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637676"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="52525-103">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="52525-103">C# preprocessor directives</span></span>

<span data-ttu-id="52525-104">Derleyicinin ayrı bir önişlemcisi olmasa da, bu bölümde açıklanan yönergeler bir gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="52525-104">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="52525-105">Koşullu derlemede yardımcı olması için bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52525-105">You use them to help in conditional compilation.</span></span> <span data-ttu-id="52525-106">C ve C++ yönergelerinden farklı olarak, bu yönergeleri makrolar oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="52525-106">Unlike C and C++ directives, you can't use these directives to create macros.</span></span> <span data-ttu-id="52525-107">Bir Önişlemci yönergesi, bir satırdaki tek yönerge olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52525-107">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="nullable-context"></a><span data-ttu-id="52525-108">Null yapılabilir bağlam</span><span class="sxs-lookup"><span data-stu-id="52525-108">Nullable context</span></span>

<span data-ttu-id="52525-109">`#nullable`Önişlemci yönergesi *null yapılabilir ek açıklama bağlamını* ve *null yapılabilir uyarı bağlamını* ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-109">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="52525-110">Bu yönerge, null yapılabilir ek açıklamaların geçerli olup olmadığını ve null olabilme uyarılarının verilip verilmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="52525-110">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="52525-111">Her bağlam *devre dışı* ya da *etkin*.</span><span class="sxs-lookup"><span data-stu-id="52525-111">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="52525-112">Her iki içerik de proje düzeyinde belirtilebilir (C# kaynak kodu dışında).</span><span class="sxs-lookup"><span data-stu-id="52525-112">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="52525-113">`#nullable`Yönergesi ek açıklamanın ve uyarı bağlamlarını denetler ve proje düzeyi ayarlarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="52525-113">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="52525-114">Bir yönerge, başka bir yönerge tarafından geçersiz kılınana kadar veya kaynak dosyanın sonuna kadar denetlediği bağlamı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-114">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="52525-115">Yönergelerin etkisi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="52525-115">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="52525-116">`#nullable disable`: Nullable ek açıklama ve uyarı bağlamlarını *devre dışı* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-116">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="52525-117">`#nullable enable`: Null yapılabilir ek açıklama ve uyarı bağlamlarını *etkin* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-117">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="52525-118">`#nullable restore`: Proje ayarlarına Nullable ek açıklama ve uyarı bağlamlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="52525-118">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="52525-119">`#nullable disable annotations`: Nullable ek açıklama bağlamını *devre dışı* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-119">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="52525-120">`#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını *etkin* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-120">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="52525-121">`#nullable restore annotations`: Null yapılabilir ek açıklama bağlamını proje ayarlarına geri yükler.</span><span class="sxs-lookup"><span data-stu-id="52525-121">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="52525-122">`#nullable disable warnings`: Nullable uyarı bağlamını *devre dışı* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-122">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="52525-123">`#nullable enable warnings`: Null yapılabilir uyarı bağlamını *etkin* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52525-123">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="52525-124">`#nullable restore warnings`: Proje ayarlarına Nullable uyarı bağlamını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="52525-124">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="conditional-compilation"></a><span data-ttu-id="52525-125">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="52525-125">Conditional compilation</span></span>

<span data-ttu-id="52525-126">Koşullu derlemeyi denetlemek için dört Önişlemci yönergesi kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="52525-126">You use four preprocessor directives to control conditional compilation:</span></span>

- <span data-ttu-id="52525-127">`#if`: Kodun yalnızca belirtilen sembol tanımlanmışsa derlenmesi durumunda, koşullu bir derleme açılır.</span><span class="sxs-lookup"><span data-stu-id="52525-127">`#if`: Opens a conditional compilation, where code is compiled only if the specified symbol is defined.</span></span>
- <span data-ttu-id="52525-128">`#elif`: Önceki koşullu derlemeyi kapatır ve belirtilen simgenin tanımlanması halinde yeni bir koşullu derleme açar.</span><span class="sxs-lookup"><span data-stu-id="52525-128">`#elif`: Closes the preceding conditional compilation and opens a new conditional compilation based on if the specified symbol is defined.</span></span>
- <span data-ttu-id="52525-129">`#else`: Önceki koşullu derlemeyi kapatır ve önceki belirtilen sembol tanımlanmamışsa yeni bir koşullu derleme açar.</span><span class="sxs-lookup"><span data-stu-id="52525-129">`#else`: Closes the preceding conditional compilation and opens a new conditional compilation if the previous specified symbol isn't defined.</span></span>
- <span data-ttu-id="52525-130">`#endif`: Önceki koşullu derlemeyi kapatır.</span><span class="sxs-lookup"><span data-stu-id="52525-130">`#endif`: Closes the preceding conditional compilation.</span></span>

<span data-ttu-id="52525-131">C# derleyicisi bir yönerge bulduğunda ve `#if` sonunda bir `#endif` yönerge ile, yalnızca belirtilen sembol tanımlanmışsa, yönergeler arasındaki kodu derler.</span><span class="sxs-lookup"><span data-stu-id="52525-131">When the C# compiler finds an `#if` directive, followed eventually by an `#endif` directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="52525-132">C ve C++ ' dan farklı olarak, bir simgeye sayısal değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="52525-132">Unlike C and C++, you can't assign a numeric value to a symbol.</span></span> <span data-ttu-id="52525-133">`#if`C# ' deki ifade, Boolean ve yalnızca sembolün tanımlanıp tanımlanmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="52525-133">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="52525-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="52525-134">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="52525-135">Değerlerini veya test etmek için İşleçleri [ `==` (eşitlik)](operators/equality-operators.md#equality-operator-) ve [ `!=` (eşitsizlik)](operators/equality-operators.md#inequality-operator-) kullanabilirsiniz [`bool`](builtin-types/bool.md) `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="52525-135">You can use the operators [`==` (equality)](operators/equality-operators.md#equality-operator-) and [`!=` (inequality)](operators/equality-operators.md#inequality-operator-) to test for the [`bool`](builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="52525-136">`true` simgenin tanımlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52525-136">`true` means the symbol is defined.</span></span> <span data-ttu-id="52525-137">İfade, `#if DEBUG` ile aynı anlama sahiptir `#if (DEBUG == true)` .</span><span class="sxs-lookup"><span data-stu-id="52525-137">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="52525-138">Birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için [ `&&` (ve)](operators/boolean-logical-operators.md#conditional-logical-and-operator-), [ `||` (veya)](operators/boolean-logical-operators.md#conditional-logical-or-operator-)ve [ `!` (Not](operators/boolean-logical-operators.md#logical-negation-operator-) ) işleçlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52525-138">You can use the [`&&` (and)](operators/boolean-logical-operators.md#conditional-logical-and-operator-), [`||` (or)](operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [`!` (not)](operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="52525-139">Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52525-139">You can also group symbols and operators with parentheses.</span></span>

<span data-ttu-id="52525-140">`#if`,,, `#else` `#elif` `#endif` `#define` ve `#undef` yönergeleriyle birlikte, bir veya daha fazla simgenin varlığına göre kodu dahil etmenize veya dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-140">`#if`, along with the `#else`, `#elif`, `#endif`, `#define`, and `#undef` directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="52525-141">Koşullu derleme, hata ayıklama derlemesi için kod derlerken veya belirli bir yapılandırma için derlenirken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-141">Conditional compilation can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="52525-142">Yönergeyle başlayan koşullu bir yönerge `#if` , açıkça bir yönergeyle sonlandırılmalıdır `#endif` .</span><span class="sxs-lookup"><span data-stu-id="52525-142">A conditional directive beginning with an `#if` directive must explicitly be terminated with an `#endif` directive.</span></span> <span data-ttu-id="52525-143">`#define` bir sembol tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-143">`#define` lets you define a symbol.</span></span> <span data-ttu-id="52525-144">Sembol, yönergeye geçirilen ifade olarak kullanıldığında ifadesi olarak `#if` değerlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="52525-144">By using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span> <span data-ttu-id="52525-145">Ayrıca, [**Definesabitleri**](compiler-options/language.md#defineconstants) derleyici seçeneğiyle bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52525-145">You can also define a symbol with the [**DefineConstants**](compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="52525-146">İle bir simge tanımlayabilirsiniz `#undef` .</span><span class="sxs-lookup"><span data-stu-id="52525-146">You can undefine a symbol with `#undef`.</span></span> <span data-ttu-id="52525-147">İle oluşturulan sembolün kapsamı, `#define` tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="52525-147">The scope of a symbol created with `#define` is the file in which it was defined.</span></span> <span data-ttu-id="52525-148">**Definesabitleri** veya ile tanımladığınız bir sembol `#define` aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="52525-148">A symbol that you define with **DefineConstants** or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="52525-149">Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="52525-149">That is, a variable name shouldn't be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="52525-150">`#elif` bileşik bir koşullu yönerge oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-150">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="52525-151">`#elif`İfade, `#if` ne önce ne de önceki, isteğe bağlı bir `#elif` yönerge ifadesi olarak değerlendiriliyorsa değerlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="52525-151">The `#elif` expression will be evaluated if neither the preceding `#if` nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="52525-152">Bir `#elif` ifade olarak değerlendirilirse `true` , derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="52525-152">If an `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="52525-153">Örnek:</span><span class="sxs-lookup"><span data-stu-id="52525-153">For example:</span></span>

```csharp
#define VC7
//...
#if debug
    Console.WriteLine("Debug build");
#elif VC7
    Console.WriteLine("Visual Studio 7");
#endif
```

<span data-ttu-id="52525-154">`#else` , önceki `#if` veya (isteğe bağlı) `#elif` yönergelerinden hiçbiri olarak değerlendiriyorsa `true` , derleyici, ve arasındaki tüm kodları değerlendirmek için bileşik `#else` bir koşullu yönerge oluşturmanıza olanak sağlar `#endif` .</span><span class="sxs-lookup"><span data-stu-id="52525-154">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding `#if` or (optional) `#elif` directives evaluate to `true`, the compiler will evaluate all code between `#else` and the next `#endif`.</span></span> <span data-ttu-id="52525-155">`#endif`(#endif) sonraki ön işlemci yönergesi olmalıdır `#else` .</span><span class="sxs-lookup"><span data-stu-id="52525-155">`#endif`(#endif) must be the next preprocessor directive after `#else`.</span></span>

<span data-ttu-id="52525-156">`#endif` yönergeyle başlayan bir koşul yönergesinin sonunu belirtir `#if` .</span><span class="sxs-lookup"><span data-stu-id="52525-156">`#endif` specifies the end of a conditional directive, which began with the `#if` directive.</span></span>

<span data-ttu-id="52525-157">Yapı sistemi, SDK stili projelerde farklı [hedef çerçeveleri](../../standard/frameworks.md) temsil eden önceden tanımlanmış ön işlemci sembolleri de farkındadır.</span><span class="sxs-lookup"><span data-stu-id="52525-157">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="52525-158">Birden fazla .NET sürümü hedefleyebilir uygulamalar oluştururken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="52525-158">They're useful when creating applications that can target more than one .NET version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="52525-159">Geleneksel, SDK olmayan projeler için, Visual Studio 'daki farklı hedef çerçeveler için koşullu derleme sembollerini projenin Özellikler sayfaları aracılığıyla el ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52525-159">For traditional, non-SDK-style projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="52525-160">Diğer önceden tanımlanmış semboller, `DEBUG` ve `TRACE` sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="52525-160">Other predefined symbols include the `DEBUG` and `TRACE` constants.</span></span> <span data-ttu-id="52525-161">Kullanarak proje için ayarlanan değerleri geçersiz kılabilirsiniz `#define` .</span><span class="sxs-lookup"><span data-stu-id="52525-161">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="52525-162">Örneğin, hata ayıklama sembolü, derleme yapılandırma özelliklerine ("hata ayıklama" veya "yayın" modu) göre otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="52525-162">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

<span data-ttu-id="52525-163">Aşağıdaki örnek, `MYTEST` bir dosyanın üzerinde bir sembol tanımlanacağını ve sonra ve simgelerinin değerlerini test etmek için size gösterir `MYTEST` `DEBUG` .</span><span class="sxs-lookup"><span data-stu-id="52525-163">The following example shows you how to define a `MYTEST` symbol on a file and then test the values of the `MYTEST` and `DEBUG` symbols.</span></span> <span data-ttu-id="52525-164">Bu örneğin çıktısı, projeyi **hata ayıklama** veya **Sürüm** yapılandırma modunda derdığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="52525-164">The output of this example depends on whether you built the project on **Debug** or **Release** configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="52525-165">Aşağıdaki örnekte, mümkünse daha yeni API 'Leri kullanabilmeniz için farklı hedef çerçeveler için nasıl test yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="52525-165">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="defining-symbols"></a><span data-ttu-id="52525-166">Sembolleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="52525-166">Defining symbols</span></span>

<span data-ttu-id="52525-167">Koşullu derleme için sembolleri tanımlamak veya tanımlamak üzere aşağıdaki iki Önişlemci yönergesi kullanın:</span><span class="sxs-lookup"><span data-stu-id="52525-167">You use the following two preprocessor directives to define or undefine symbols for conditional compilation:</span></span>

- <span data-ttu-id="52525-168">`#define`: Bir sembol tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52525-168">`#define`: Define a symbol.</span></span>
- <span data-ttu-id="52525-169">`#undef`: bir sembol tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52525-169">`#undef`: undefine a symbol.</span></span>

<span data-ttu-id="52525-170">`#define`Bir sembol tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="52525-170">You use `#define` to define a symbol.</span></span> <span data-ttu-id="52525-171">Simgesini yönergeye geçirilen ifade olarak kullandığınızda `#if` , `true` Aşağıdaki örnekte gösterildiği gibi ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="52525-171">When you use the symbol as the expression that's passed to the `#if` directive, the expression will evaluate to `true`, as the following example shows:</span></span>

 ```csharp
 #define VERBOSE

#if VERBOSE
    Console.WriteLine("Verbose output version");
#endif

 ```

> [!NOTE]
> <span data-ttu-id="52525-172">`#define`Yönerge, genellikle C ve C++ ' da yapıldığı gibi sabit değerleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="52525-172">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="52525-173">C# ' deki sabitler, bir sınıfın veya yapının statik üyeleri olarak en iyi şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="52525-173">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="52525-174">Bu tür sabitlere sahipseniz, bunları tutmak için ayrı bir "sabitler" sınıfı oluşturmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="52525-174">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>

<span data-ttu-id="52525-175">Simgeler, derleme koşullarını belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-175">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="52525-176">Ya da simgesiyle test edebilirsiniz `#if` `#elif` .</span><span class="sxs-lookup"><span data-stu-id="52525-176">You can test for the symbol with either `#if` or `#elif`.</span></span> <span data-ttu-id="52525-177"><xref:System.Diagnostics.ConditionalAttribute>Koşullu derleme gerçekleştirmek için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52525-177">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span> <span data-ttu-id="52525-178">Bir sembol tanımlayabilirsiniz, ancak bir simgeye değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="52525-178">You can define a symbol, but you can't assign a value to a symbol.</span></span> <span data-ttu-id="52525-179">`#define`Ayrıca Önişlemci yönergeleri olmayan herhangi bir yönergeyi kullanmadan önce yönerge dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="52525-179">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span> <span data-ttu-id="52525-180">Ayrıca, [**Definesabitleri**](compiler-options/language.md#defineconstants) derleyici seçeneğiyle bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52525-180">You can also define a symbol with the [**DefineConstants**](compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="52525-181">İle bir simge tanımlayabilirsiniz `#undef` .</span><span class="sxs-lookup"><span data-stu-id="52525-181">You can undefine a symbol with `#undef`.</span></span>

## <a name="defining-regions"></a><span data-ttu-id="52525-182">Bölgeleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="52525-182">Defining regions</span></span>

<span data-ttu-id="52525-183">Aşağıdaki iki önişlemci yönergelerini kullanarak bir anahatta daraltılabilen kod bölgelerini tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52525-183">You can define regions of code that can be collapsed in an outline using the following two preprocessor directives:</span></span>

- <span data-ttu-id="52525-184">`#region`: Bir bölge başlatın.</span><span class="sxs-lookup"><span data-stu-id="52525-184">`#region`: Start a region.</span></span>
- <span data-ttu-id="52525-185">`#endregion`: Bölge sonu</span><span class="sxs-lookup"><span data-stu-id="52525-185">`#endregion`: End a region</span></span>

<span data-ttu-id="52525-186">`#region` kod düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="52525-186">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="52525-187">Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bir kısmına odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-187">In longer code files, it's convenient to collapse or hide one or more regions so that you can focus on the part of the file that you're currently working on.</span></span> <span data-ttu-id="52525-188">Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="52525-188">The following example shows how to define a region:</span></span>

```csharp
#region MyClass definition
public class MyClass
{
    static void Main()
    {
    }
}
#endregion
```

<span data-ttu-id="52525-189">Bir `#region` bloğun bir yönergeyle sonlandırılması gerekir `#endregion` .</span><span class="sxs-lookup"><span data-stu-id="52525-189">A `#region` block must be terminated with an `#endregion` directive.</span></span> <span data-ttu-id="52525-190">Bir `#region` blok bir blok ile çakışamaz `#if` .</span><span class="sxs-lookup"><span data-stu-id="52525-190">A `#region` block can't overlap with an `#if` block.</span></span> <span data-ttu-id="52525-191">Ancak bir blok bir `#region` blokta iç içe olabilir ve bir blok `#if` bir blok `#if` içinde iç içe olabilir `#region` .</span><span class="sxs-lookup"><span data-stu-id="52525-191">However, a `#region` block can be nested in an `#if` block, and an `#if` block can be nested in a `#region` block.</span></span>

## <a name="error-and-warning-information"></a><span data-ttu-id="52525-192">Hata ve uyarı bilgileri</span><span class="sxs-lookup"><span data-stu-id="52525-192">Error and warning information</span></span>

<span data-ttu-id="52525-193">Derleyicinin Kullanıcı tanımlı derleyici hataları ve uyarıları oluşturmasını ve aşağıdaki yönergeleri kullanarak hat bilgilerini kontrol etmek için talimat alırsınız:</span><span class="sxs-lookup"><span data-stu-id="52525-193">You instruct the compiler to generate user-defined compiler errors and warnings, and control line information using the following directives:</span></span>

- <span data-ttu-id="52525-194">`#error`: Belirtilen iletiyle derleyici hatası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="52525-194">`#error`: Generate a compiler error with a specified message.</span></span>
- <span data-ttu-id="52525-195">`#warning`: Belirli bir iletiyle bir derleyici uyarısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="52525-195">`#warning`: Generate a compiler warning, with a specific message.</span></span>
- <span data-ttu-id="52525-196">`#line`: Derleyici iletileriyle yazdırılan satır numarasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="52525-196">`#line`: Change the line number printed with compiler messages.</span></span>

<span data-ttu-id="52525-197">`#error` kodunuzda belirli bir konumdan [CS1029](compiler-messages/cs1029.md) Kullanıcı tanımlı bir hata oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-197">`#error` lets you generate a [CS1029](compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="52525-198">Örnek:</span><span class="sxs-lookup"><span data-stu-id="52525-198">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="52525-199">Derleyici `#error version` özel bir şekilde davranır ve bir derleyici hatası, CS8304, kullanılan derleyici ve dil sürümlerini içeren bir ileti ile rapor eder.</span><span class="sxs-lookup"><span data-stu-id="52525-199">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

<span data-ttu-id="52525-200">`#warning` kodunuzda belirli bir konumdan bir [CS1030](../misc/cs1030.md) düzeyinde bir derleyici uyarısı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-200">`#warning` lets you generate a [CS1030](../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="52525-201">Örnek:</span><span class="sxs-lookup"><span data-stu-id="52525-201">For example:</span></span>

```csharp
#warning Deprecated code in this method.
```

<span data-ttu-id="52525-202">`#line` Derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) hata ve uyarı için dosya adı çıktısını değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="52525-202">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="52525-203">Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="52525-203">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="52525-204">`#line 200`Yönerge, sonraki satırın numarasını 200 (varsayılan değer #6) olarak zorlar ve sonraki `#line` yönergeye kadar dosya adı "özel" olarak raporlanır.</span><span class="sxs-lookup"><span data-stu-id="52525-204">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="52525-205">`#line default`Yönerge, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmayla satır numaralandırmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="52525-205">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="52525-206">Derleme aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="52525-206">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

<span data-ttu-id="52525-207">`#line`Yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-207">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="52525-208">Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından özgün satır numaralandırmasının benzetimini yapabilirsiniz `#line` .</span><span class="sxs-lookup"><span data-stu-id="52525-208">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="52525-209">`#line hidden`Yönerge, hata ayıklayıcıdaki ardışık satırları gizler, örneğin, Geliştirici kod içinde, bir `#line hidden` ve sonraki `#line` yönerge (başka bir yönerge olmadığı varsayılarak) arasında herhangi bir satır `#line hidden` üzerinden ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="52525-209">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it isn't another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="52525-210">Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-210">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="52525-211">ASP.NET bu özelliğin birincil tüketicisi olsa da, bu, büyük olasılıkla daha fazla kaynak oluşturanlar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-211">Although ASP.NET is the primary consumer of this feature, it's likely that more source generators will make use of it.</span></span>

<span data-ttu-id="52525-212">`#line hidden`Yönerge, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="52525-212">A `#line hidden` directive doesn't affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="52525-213">Diğer bir deyişle, derleyici gizli bir blokta bir hata bulursa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="52525-213">That is, if the compiler finds an error in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="52525-214">`#line filename`Yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="52525-214">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="52525-215">Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52525-215">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="52525-216">Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="52525-216">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="52525-217">Aşağıdaki örnek, hata ayıklayıcının koddaki gizli satırları nasıl yoksaydığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="52525-217">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="52525-218">Örneği çalıştırdığınızda üç satırlık metin görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52525-218">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="52525-219">Ancak, örnekte gösterildiği gibi bir kesme noktası ayarladığınızda ve kodun içinde ilerlemek için F10 'e vuruladığınızda, hata ayıklayıcı gizli çizgiyi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="52525-219">However, when you set a break point, as shown in the example, and hit F10 to step through the code, the debugger ignores the hidden line.</span></span> <span data-ttu-id="52525-220">Gizli satırda bir kesme noktası ayarlamış olsanız bile, hata ayıklayıcı yine de yok sayılacak.</span><span class="sxs-lookup"><span data-stu-id="52525-220">Even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="pragmas"></a><span data-ttu-id="52525-221">Pragmalar</span><span class="sxs-lookup"><span data-stu-id="52525-221">Pragmas</span></span>

<span data-ttu-id="52525-222">`#pragma` Derleyicinin göründüğü dosyanın derlenmesi için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-222">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="52525-223">Yönergeler derleyici tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="52525-223">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="52525-224">Diğer bir deyişle, `#pragma` özel ön işleme yönergeleri oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="52525-224">In other words, you can't use `#pragma` to create custom preprocessing instructions.</span></span>
  
- <span data-ttu-id="52525-225">[`#pragma warning`](#pragma-warning): Uyarıları etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="52525-225">[`#pragma warning`](#pragma-warning): Enable or disable warnings.</span></span>
- <span data-ttu-id="52525-226">[`#pragma checksum`](#pragma-checksum): Sağlama toplamı oluştur.</span><span class="sxs-lookup"><span data-stu-id="52525-226">[`#pragma checksum`](#pragma-checksum): Generate a checksum.</span></span>

```csharp
#pragma pragma-name pragma-arguments
```

<span data-ttu-id="52525-227">Burada `pragma-name` tanınan bir pragma 'ın adıdır ve `pragma-arguments` pragmaya özgü bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="52525-227">Where `pragma-name` is the name of a recognized pragma and `pragma-arguments` is the pragma-specific arguments.</span></span>

### <a name="pragma-warning"></a><span data-ttu-id="52525-228">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="52525-228">#pragma warning</span></span>

<span data-ttu-id="52525-229">`#pragma warning` Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="52525-229">`#pragma warning` can enable or disable certain warnings.</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

<span data-ttu-id="52525-230">Burada `warning-list` , uyarı numaralarının virgülle ayrılmış bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="52525-230">Where `warning-list` is a comma-separated list of warning numbers.</span></span> <span data-ttu-id="52525-231">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="52525-231">The "CS" prefix is optional.</span></span> <span data-ttu-id="52525-232">Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="52525-232">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="52525-233">Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.</span><span class="sxs-lookup"><span data-stu-id="52525-233">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

<span data-ttu-id="52525-234">`disable`Kaynak dosyanın bir sonraki satırından başlayarak etkisini alır.</span><span class="sxs-lookup"><span data-stu-id="52525-234">The `disable` takes effect beginning on the next line of the source file.</span></span> <span data-ttu-id="52525-235">Uyarı, izleyen satıra geri yüklenir `restore` .</span><span class="sxs-lookup"><span data-stu-id="52525-235">The warning is restored on the line following the `restore`.</span></span> <span data-ttu-id="52525-236">`restore`Dosyada yoksa, uyarılar aynı derlemede bulunan sonraki dosyaların ilk satırında varsayılan durumlarına geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="52525-236">If there's no `restore` in the file, the warnings are restored to their default state at the first line of any later files in the same compilation.</span></span>

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

### <a name="pragma-checksum"></a><span data-ttu-id="52525-237">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="52525-237">#pragma checksum</span></span>

<span data-ttu-id="52525-238">ASP.NET sayfalarında hata ayıklamaya yardımcı olmak için kaynak dosyaları için sağlama toplamı üretir.</span><span class="sxs-lookup"><span data-stu-id="52525-238">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>

```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"
```

<span data-ttu-id="52525-239">, `"filename"` Değişiklik veya güncelleştirme için izlemeyi gerektiren dosyanın adı, `"{guid}"` karma algoritmanın genel benzersiz TANıMLAYıCıSıDıR (GUID) ve `"checksum_bytes"` sağlama toplamı baytlarını temsil eden onaltılık basamakların dizesidir.</span><span class="sxs-lookup"><span data-stu-id="52525-239">Where `"filename"` is the name of the file that requires monitoring for changes or updates, `"{guid}"` is the Globally Unique Identifier (GUID) for the hash algorithm, and `"checksum_bytes"` is the string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="52525-240">Çift sayıda onaltılık basamak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52525-240">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="52525-241">Tek sayıda basamak derleme zamanı uyarısına neden olur ve yönerge yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="52525-241">An odd number of digits results in a compile-time warning, and the directive is ignored.</span></span>

<span data-ttu-id="52525-242">Visual Studio hata ayıklayıcı, her zaman doğru kaynağı bulmasını sağlamak için bir sağlama toplamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="52525-242">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="52525-243">Derleyici, kaynak dosya için sağlama toplamını hesaplar ve sonra çıktıyı program veritabanı (PDB) dosyasına yayar.</span><span class="sxs-lookup"><span data-stu-id="52525-243">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="52525-244">Hata ayıklayıcı daha sonra kaynak dosya için hesapladığı sağlama toplamıyla karşılaştırmak için PDB 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="52525-244">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>

<span data-ttu-id="52525-245">Hesaplanan sağlama toplamı,. aspx dosyası yerine oluşturulan kaynak dosya için olduğundan, bu çözüm ASP.NET projelerinde çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="52525-245">This solution doesn't work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="52525-246">Bu sorunu gidermek için `#pragma checksum` ASP.NET sayfaları için sağlama toplamı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="52525-246">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>

<span data-ttu-id="52525-247">Visual C# içinde bir ASP.NET projesi oluşturduğunuzda oluşturulan kaynak dosya, kaynağın oluşturulduğu. aspx dosyası için bir sağlama toplamı içerir.</span><span class="sxs-lookup"><span data-stu-id="52525-247">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="52525-248">Derleyici daha sonra bu bilgileri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="52525-248">The compiler then writes this information into the PDB file.</span></span>

<span data-ttu-id="52525-249">Derleyici `#pragma checksum` dosyada bir yönerge bulamazsa, sağlama toplamını hesaplar ve DEĞERI pdb dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="52525-249">If the compiler doesn't find a `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>

```csharp
class TestClass
{
    static int Main()
    {
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum
    }
}
```
