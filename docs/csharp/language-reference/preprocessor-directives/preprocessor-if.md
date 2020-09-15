---
description: '#If Önişlemci yönergesi-C# başvurusu'
title: '#If Önişlemci yönergesi-C# başvurusu'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: dc3e235db49279691203a0db4d124239fb972c69
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065246"
---
# <a name="if-c-reference"></a><span data-ttu-id="27409-103">#if (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="27409-103">#if (C# reference)</span></span>

<span data-ttu-id="27409-104">C# derleyicisi bir `#if` yönergeyle karşılaştığında, sonunda bir [#endif](preprocessor-endif.md) yönergesi ile, yalnızca belirtilen sembol tanımlanmışsa, yönergeler arasındaki kodu derler.</span><span class="sxs-lookup"><span data-stu-id="27409-104">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="27409-105">C ve C++ ' dan farklı olarak, bir simgeye sayısal değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="27409-105">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="27409-106">`#if`C# ' deki ifade, Boolean ve yalnızca sembolün tanımlanıp tanımlanmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="27409-106">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="27409-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27409-107">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="27409-108">İşleçleri [==](../operators/equality-operators.md#equality-operator-) (eşitlik) ve [! =](../operators/equality-operators.md#inequality-operator-) (eşitsizlik) yalnızca [bool](../builtin-types/bool.md) değerlerini veya test etmek için kullanabilirsiniz `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="27409-108">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="27409-109">`true` simgenin tanımlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="27409-109">`true` means the symbol is defined.</span></span> <span data-ttu-id="27409-110">İfade, `#if DEBUG` ile aynı anlama sahiptir `#if (DEBUG == true)` .</span><span class="sxs-lookup"><span data-stu-id="27409-110">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="27409-111">[&&  (ve)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;  (veya)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)ve! kullanabilirsiniz. [ (Not)](../operators/boolean-logical-operators.md#logical-negation-operator-) birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için işleçler.</span><span class="sxs-lookup"><span data-stu-id="27409-111">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="27409-112">Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27409-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="27409-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27409-113">Remarks</span></span>

<span data-ttu-id="27409-114">`#if`[#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)ve [#undef](preprocessor-undef.md) yönergeleriyle birlikte, bir veya daha fazla simgenin varlığına göre kodu dahil etmenize veya dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="27409-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="27409-115">Bu, hata ayıklama derlemesi için kod derlerken veya belirli bir yapılandırma için derlenirken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="27409-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="27409-116">Yönergeyle başlayan koşullu bir yönerge `#if` , açıkça bir yönergeyle sonlandırılmalıdır `#endif` .</span><span class="sxs-lookup"><span data-stu-id="27409-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="27409-117">`#define` bir sembol tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="27409-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="27409-118">Ardından, simgesini yönergeye geçirilen ifade olarak kullanarak ifade olarak `#if` değerlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="27409-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="27409-119">Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27409-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="27409-120">[#Undef](preprocessor-undef.md)bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27409-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="27409-121">Veya ile tanımladığınız bir sembol `-define` `#define` aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="27409-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="27409-122">Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="27409-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="27409-123">İle oluşturulan sembolün kapsamı, `#define` tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="27409-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="27409-124">Yapı sistemi, SDK stili projelerde farklı [hedef çerçeveleri](../../../standard/frameworks.md) temsil eden önceden tanımlanmış ön işlemci sembolleri de farkındadır.</span><span class="sxs-lookup"><span data-stu-id="27409-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="27409-125">Birden fazla .NET sürümü hedefleyebilir uygulamalar oluştururken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="27409-125">They're useful when creating applications that can target more than one .NET version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="27409-126">Geleneksel, SDK olmayan projeler için, Visual Studio 'daki farklı hedef çerçeveler için koşullu derleme sembollerini projenin Özellikler sayfaları aracılığıyla el ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="27409-126">For traditional, non-SDK-style projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="27409-127">Önceden tanımlanmış diğer semboller, hata ayıklama ve Izleme sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="27409-127">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="27409-128">Kullanarak proje için ayarlanan değerleri geçersiz kılabilirsiniz `#define` .</span><span class="sxs-lookup"><span data-stu-id="27409-128">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="27409-129">Örneğin, hata ayıklama sembolü, derleme yapılandırma özelliklerine ("hata ayıklama" veya "yayın" modu) göre otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="27409-129">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="27409-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="27409-130">Examples</span></span>

<span data-ttu-id="27409-131">Aşağıdaki örnek, bir dosya üzerinde MYTEST sembolünü nasıl tanımlacağınızı ve sonra MYTEST ve hata ayıklama simgelerinin değerlerini test etmek için size gösterir.</span><span class="sxs-lookup"><span data-stu-id="27409-131">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="27409-132">Bu örneğin çıktısı, projeyi hata ayıklama veya sürüm yapılandırma modunda derdığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="27409-132">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="27409-133">Aşağıdaki örnekte, mümkünse daha yeni API 'Leri kullanabilmeniz için farklı hedef çerçeveler için nasıl test yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="27409-133">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="27409-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27409-134">See also</span></span>

- [<span data-ttu-id="27409-135">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="27409-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="27409-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="27409-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="27409-137">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="27409-137">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="27409-138">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="27409-138">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
