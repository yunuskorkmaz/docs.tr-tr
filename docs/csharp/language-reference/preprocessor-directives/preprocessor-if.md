---
title: '#If Önişlemci yönergesi- C# başvuru'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d0297094fbb8098b706cb8c6338fa123afc0753b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605693"
---
# <a name="if-c-reference"></a><span data-ttu-id="187c6-102">#if (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="187c6-102">#if (C# Reference)</span></span>

<span data-ttu-id="187c6-103">C# Derleyici bir `#if` yönergeyle karşılaştığında, sonunda bir [#endif](preprocessor-endif.md) yönergesi ile, yalnızca belirtilen sembol tanımlanmışsa, yönergeler arasındaki kodu derler.</span><span class="sxs-lookup"><span data-stu-id="187c6-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="187c6-104">C ve C++' nin aksine, bir simgeye sayısal değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="187c6-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="187c6-105">İçindeki C# #if deyimleri Boolean olur ve yalnızca sembolün tanımlanıp tanımlanmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="187c6-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="187c6-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="187c6-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="187c6-107">Yalnızca [true](../keywords/true-literal.md) veya [false](../keywords/false-literal.md)için [==](../operators/equality-operators.md#equality-operator-) test etmek amacıyla işleçleri (eşitlik) ve [! =](../operators/equality-operators.md#inequality-operator-) (eşitsizlik) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="187c6-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true-literal.md) or [false](../keywords/false-literal.md).</span></span> <span data-ttu-id="187c6-108">Doğru, simgenin tanımlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="187c6-108">True means the symbol is defined.</span></span> <span data-ttu-id="187c6-109">İfade `#if DEBUG` , ile `#if (DEBUG == true)`aynı anlama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="187c6-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="187c6-110">İşleçlerini [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (ve), [](../operators/boolean-logical-operators.md#logical-negation-operator-) [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (veya) ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="187c6-110">You can use the operators [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or), and [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span></span> <span data-ttu-id="187c6-111">(değil) birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="187c6-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="187c6-112">Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="187c6-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="187c6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="187c6-113">Remarks</span></span>

<span data-ttu-id="187c6-114">`#if`[#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)ve [#undef](preprocessor-undef.md) yönergeleriyle birlikte, bir veya daha fazla simgenin varlığına göre kodu dahil etmenize veya dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="187c6-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="187c6-115">Bu, hata ayıklama derlemesi için kod derlerken veya belirli bir yapılandırma için derlenirken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="187c6-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="187c6-116">`#if` Yönergeyle başlayan koşullu bir yönerge, açıkça bir `#endif` yönergeyle sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="187c6-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="187c6-117">`#define`bir sembol tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="187c6-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="187c6-118">Ardından, simgesini `#if` yönergeye geçirilen ifade olarak kullanarak ifade olarak `true`değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="187c6-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="187c6-119">Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="187c6-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="187c6-120">[#Undef](preprocessor-undef.md)bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="187c6-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="187c6-121">`-define` Veya ile`#define` tanımladığınız bir sembol aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="187c6-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="187c6-122">Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="187c6-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="187c6-123">İle `#define` oluşturulan sembolün kapsamı, tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="187c6-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="187c6-124">Yapı sistemi, farklı [hedef çerçeveleri](../../../standard/frameworks.md)temsil eden önceden tanımlanmış önişlemci sembolleri de farkındadır.</span><span class="sxs-lookup"><span data-stu-id="187c6-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="187c6-125">Birden fazla .NET uygulaması veya sürümü hedefleyebilir uygulamalar oluştururken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="187c6-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="187c6-126">Önceden tanımlanmış diğer semboller, hata ayıklama ve Izleme sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="187c6-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="187c6-127">Kullanarak `#define`proje için ayarlanan değerleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="187c6-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="187c6-128">Örneğin, hata ayıklama sembolü, derleme yapılandırma özelliklerine ("hata ayıklama" veya "yayın" modu) göre otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="187c6-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="187c6-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="187c6-129">Examples</span></span>

<span data-ttu-id="187c6-130">Aşağıdaki örnek, bir dosya üzerinde MYTEST sembolünü nasıl tanımlacağınızı ve sonra MYTEST ve hata ayıklama simgelerinin değerlerini test etmek için size gösterir.</span><span class="sxs-lookup"><span data-stu-id="187c6-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="187c6-131">Bu örneğin çıktısı, projeyi hata ayıklama veya sürüm yapılandırma modunda derdığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="187c6-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="187c6-132">Aşağıdaki örnekte, mümkünse daha yeni API 'Leri kullanabilmeniz için farklı hedef çerçeveler için nasıl test yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="187c6-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="187c6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="187c6-133">See also</span></span>

- [<span data-ttu-id="187c6-134">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="187c6-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="187c6-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="187c6-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="187c6-136">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="187c6-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="187c6-137">Nasıl yapılır: Izleme ve hata ayıklama ile koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="187c6-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
