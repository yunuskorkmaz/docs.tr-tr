---
title: '#Önişlemci yönergesi - C# başvurusu'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: b92660a69194ff2d52cd78427f73510de514ea48
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545825"
---
# <a name="if-c-reference"></a><span data-ttu-id="a6e6d-102">#if (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6e6d-102">#if (C# Reference)</span></span>

<span data-ttu-id="a6e6d-103">C# derleyicisi karşılaştığında bir `#if` yönergesi, ardından sonuç ile bir [#endif](preprocessor-endif.md) yalnızca belirtilen simge tanımlanmışsa yönergesi, bu yönergeleri arasında kod derler.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="a6e6d-104">C ve C++'ın aksine, bir sembol için sayısal bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="a6e6d-105">#İf deyiminde C#, Boole ve yalnızca veya sembol tanımlanmış olup olmadığını test eder.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="a6e6d-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a6e6d-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="a6e6d-107">İşleçleri [ == ](../operators/equality-operators.md#equality-operator-) (eşitlik) ve [! =](../operators/equality-operators.md#inequality-operator-) (yalnızca test etmek için eşitsizlik) [true](../keywords/true.md) veya [false](../keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="a6e6d-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true.md) or [false](../keywords/false.md).</span></span> <span data-ttu-id="a6e6d-108">Doğru simge tanımlanmadıysa anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-108">True means the symbol is defined.</span></span> <span data-ttu-id="a6e6d-109">Deyim `#if DEBUG` olarak aynı anlamı `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="a6e6d-110">İşleçleri [ && ](../operators/conditional-and-operator.md) (ve) [ &#124; &#124; ](../operators/conditional-or-operator.md) (veya) ve [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="a6e6d-110">You can use the operators [&&](../operators/conditional-and-operator.md) (and), [&#124;&#124;](../operators/conditional-or-operator.md) (or), and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="a6e6d-111">(birden fazla sembol tanımlı olup olmadığını değerlendirmek için değil).</span><span class="sxs-lookup"><span data-stu-id="a6e6d-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="a6e6d-112">Ayrıca, simgeler ve işleçler parantezli gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6e6d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6e6d-113">Remarks</span></span>

<span data-ttu-id="a6e6d-114">`#if`, birlikte [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), ve [#undef](preprocessor-undef.md) yönergeleri sağlar dahil veya kod üzerinde bir veya daha fazla sembolleri varlığını temel hariç tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="a6e6d-115">Kod hata ayıklama derlemesi için derleme yaparken veya belirli bir yapılandırma için derleme yaparken bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="a6e6d-116">Koşullu bir yönerge başlayarak bir `#if` yönergesi açıkça tamamlanmalıdır ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="a6e6d-117">`#define` bir sembol tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="a6e6d-118">Ardından sembolü kullanmadan tarafından geçirilen ifade olarak `#if` yönergesi, ifadenin değerlendirdiği `true`.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="a6e6d-119">Ayrıca bir simge tanımlayabilirsiniz [-tanımlama](../compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="a6e6d-120">Sahip bir simge tanımlarını Kaldır [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="a6e6d-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="a6e6d-121">İle tanımladığınız bir sembol `-define` veya `#define` aynı ada sahip bir değişken çakışmadığından.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="a6e6d-122">Diğer bir deyişle, bir değişken adı bir önişlemci yönergesine geçmemiş olmalıdır ve bir simge yalnızca bir önişlemci yönergesince değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="a6e6d-123">İle oluşturulan bir simgenin kapsamı `#define` , tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="a6e6d-124">Derleme sistemi de farklı temsil eden önceden tanımlanmış önişlemci sembolleri, farkındadır [hedef çerçeveyi](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a6e6d-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="a6e6d-125">Bunlar, birden fazla .NET uygulaması veya sürümü hedefleyen uygulamaları oluştururken kullanışlı.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="a6e6d-126">Diğer önceden tanımlanmış semboller hata ayıklama ve izleme sabitleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="a6e6d-127">Proje kullanmak için ayarlanan değerleri geçersiz kılabilirsiniz `#define`.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="a6e6d-128">Hata ayıklama sembolü, örneğin, yapı yapılandırması özelliklerini ("Debug" veya "Sürüm" modu) bağlı olarak otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="a6e6d-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a6e6d-129">Examples</span></span>

<span data-ttu-id="a6e6d-130">Aşağıdaki örnek bir dosya bir MYTEST sembolünü tanımlayın ve ardından MYTEST ve hata ayıklama sembolleri değerlerini test gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="a6e6d-131">Bu örnek çıktısı, proje hata ayıklama veya sürüm yapılandırma modunu olup oluşturulan bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="a6e6d-132">Aşağıdaki örnek, mümkün olduğunda, yeni API'leri kullanabilmek için farklı bir hedef çerçeveleri test işlemini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a6e6d-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a6e6d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6e6d-133">See also</span></span>

- [<span data-ttu-id="a6e6d-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a6e6d-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="a6e6d-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6e6d-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a6e6d-136">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a6e6d-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="a6e6d-137">Nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="a6e6d-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
