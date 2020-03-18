---
title: '#if önişlemci yönergesi - C# Referans'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899850"
---
# <a name="if-c-reference"></a><span data-ttu-id="153b0-102">#if (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="153b0-102">#if (C# reference)</span></span>

<span data-ttu-id="153b0-103">C# derleyicisi bir `#if` yönergeyle karşılaştığında ve ardından [bir #endif](preprocessor-endif.md) yönergesi takip ettiğinde, kodu yalnızca belirtilen sembol tanımlanırsa yönergeler arasında derler.</span><span class="sxs-lookup"><span data-stu-id="153b0-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="153b0-104">C ve C++'ın aksine, bir sembole sayısal değer atamazsınız.</span><span class="sxs-lookup"><span data-stu-id="153b0-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="153b0-105">`#if` C# ifadesi Boolean'dır ve yalnızca sembolün tanımlanıp tanımlanmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="153b0-105">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="153b0-106">Örnek:</span><span class="sxs-lookup"><span data-stu-id="153b0-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="153b0-107">[==](../operators/equality-operators.md#equality-operator-) İşleçleri (eşitlik) ve [!=](../operators/equality-operators.md#inequality-operator-) (eşitsizlik) yalnızca [bool](../builtin-types/bool.md) değerlerini `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="153b0-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="153b0-108">`true`sembolün tanımlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="153b0-108">`true` means the symbol is defined.</span></span> <span data-ttu-id="153b0-109">İfade `#if DEBUG` , `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="153b0-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="153b0-110">[&& (ve)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-)kullanabilirsiniz, [&#124;&#124; (veya)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), ve [! (değil)](../operators/boolean-logical-operators.md#logical-negation-operator-) birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için işleçler.</span><span class="sxs-lookup"><span data-stu-id="153b0-110">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="153b0-111">Sembolleri ve işleçleri parantez içinde de gruplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="153b0-111">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="153b0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="153b0-112">Remarks</span></span>

<span data-ttu-id="153b0-113">`#if`, [#else,](preprocessor-else.md) [#elif,](preprocessor-elif.md) [#endif,](preprocessor-endif.md) [#define](preprocessor-define.md)ve [#undef](preprocessor-undef.md) yönergeleri yle birlikte, bir veya daha fazla sembolün varlığına bağlı olarak kod eklemenize veya hariç tutmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="153b0-113">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="153b0-114">Bu, hata ayıklama yapısı için kod derlerken veya belirli bir yapılandırma için derleme yaparken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="153b0-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="153b0-115">Bir `#if` yönergeyle başlayan koşullu bir yönerge, bir `#endif` yönergeyle açıkça sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="153b0-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="153b0-116">`#define`bir sembol tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="153b0-116">`#define` lets you define a symbol.</span></span> <span data-ttu-id="153b0-117">Daha sonra ifade `#if` yönergeye geçti olarak sembolü kullanarak, `true`ifade değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="153b0-117">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="153b0-118">[-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir sembol de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="153b0-118">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="153b0-119">Bir sembolü [#undef](preprocessor-undef.md)ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="153b0-119">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="153b0-120">Tanımladığınız `-define` veya tanımladığınız `#define` bir sembol, aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="153b0-120">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="153b0-121">Diğer bir diğer adıyla, bir değişken adı bir önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir önişlemci yönergesi tarafından değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="153b0-121">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="153b0-122">Oluşturulan `#define` bir sembolün kapsamı, oluşturulduğu dosyadır.</span><span class="sxs-lookup"><span data-stu-id="153b0-122">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="153b0-123">Yapı sistemi, SDK tarzı projelerde farklı [hedef çerçeveleri](../../../standard/frameworks.md) temsil eden önceden tanımlanmış önişlemci sembollerinin de farkındadır.</span><span class="sxs-lookup"><span data-stu-id="153b0-123">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="153b0-124">Birden fazla .NET uygulamasını veya sürümünü hedefleyen uygulamalar oluştururken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="153b0-124">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="153b0-125">Geleneksel .NET Framework projeleri için, Visual Studio'daki farklı hedef çerçeveler için koşullu derleme sembollerini projenin özellikleri sayfaları üzerinden el ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="153b0-125">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="153b0-126">Önceden tanımlanmış diğer semboller de BUG ve TRACE sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="153b0-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="153b0-127">Proje için ayarlanan değerleri kullanarak `#define`geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="153b0-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="153b0-128">Örneğin HATA Ayıklama simgesi, yapı yapılandırma özelliklerinize ("Hata Ayıklama" veya "Sürüm" modu) bağlı olarak otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="153b0-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="153b0-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="153b0-129">Examples</span></span>

<span data-ttu-id="153b0-130">Aşağıdaki örnek, bir dosyada MYTEST simgesini nasıl tanımlayabileceğinizi ve ardından MYTEST ve Hata Ayıklama simgelerinin değerlerini nasıl sınadığınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="153b0-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="153b0-131">Bu örneğin çıktısı, projeyi Hata Ayıklama veya Sürüm yapılandırma modunda oluşturup oluşturamadığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="153b0-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="153b0-132">Aşağıdaki örnek, mümkün olduğunda daha yeni API'leri kullanabilmeniz için farklı hedef çerçeveleri nasıl sınadığınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="153b0-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="153b0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="153b0-133">See also</span></span>

- [<span data-ttu-id="153b0-134">C# Referans</span><span class="sxs-lookup"><span data-stu-id="153b0-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="153b0-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="153b0-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="153b0-136">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="153b0-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="153b0-137">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="153b0-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
