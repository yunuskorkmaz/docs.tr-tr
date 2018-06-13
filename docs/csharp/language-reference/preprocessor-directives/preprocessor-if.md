---
title: '#varsa önişlemci yönergesi (C# Başvurusu)'
ms.date: 02/13/2017
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 2ae0af6971dbf549b52e8168e035d8582bdab61d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287689"
---
# <a name="if-c-reference"></a><span data-ttu-id="06428-102">#if (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="06428-102">#if (C# Reference)</span></span>

<span data-ttu-id="06428-103">C# Derleyici karşılaştığında bir `#if` yönergesi, ardından sonunda göre bir [#endif](preprocessor-endif.md) yalnızca belirtilen simgeyi tanımlanırsa yönerge, bu yönergeleri arasında yer alan kodunu derler.</span><span class="sxs-lookup"><span data-stu-id="06428-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="06428-104">C ve C++ aksine, bir simgeye sayısal bir değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="06428-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="06428-105">C# #if ifade Boolean ve yalnızca simgenin veya tanımlanmış olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="06428-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="06428-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="06428-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="06428-107">İşleçleri kullanabilirsiniz [ == ](../operators/equality-comparison-operator.md) (eşitlik) ve [! =](../operators/not-equal-operator.md) (yalnızca sınamak için eşitsizlik) [true](../keywords/true.md) veya [false](../keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="06428-107">You can use the operators [==](../operators/equality-comparison-operator.md) (equality) and [!=](../operators/not-equal-operator.md) (inequality) only to test for [true](../keywords/true.md) or [false](../keywords/false.md).</span></span> <span data-ttu-id="06428-108">TRUE simgenin tanımlanan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06428-108">True means the symbol is defined.</span></span> <span data-ttu-id="06428-109">Deyim `#if DEBUG` aynı anlamı taşır `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="06428-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="06428-110">İşleçleri kullanabilirsiniz [ && ](../operators/conditional-and-operator.md) (ve) [ &#124; &#124; ](../operators/conditional-or-operator.md) (veya) ve [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="06428-110">You can use the operators [&&](../operators/conditional-and-operator.md) (and), [&#124;&#124;](../operators/conditional-or-operator.md) (or), and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="06428-111">(birden çok simgeleri tanımlı olup olmadığını değerlendirmek için değil).</span><span class="sxs-lookup"><span data-stu-id="06428-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="06428-112">Ayrıca, simgeler ve parantez işleçlerle de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06428-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="06428-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06428-113">Remarks</span></span>

<span data-ttu-id="06428-114">`#if`, birlikte [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), ve [#undef](preprocessor-undef.md) yönergeleri sağlar içerebilir veya bir veya daha fazla simgeleri varlığını göre kod dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06428-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="06428-115">Hata ayıklama derlemesi kodunu derlerken veya belirli bir yapılandırma için derleme sırasında bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="06428-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="06428-116">Koşullu bir yönerge başlayarak bir `#if` yönergesi açıkça bitirilmelidir ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="06428-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="06428-117">`#define` bir simge tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="06428-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="06428-118">Geçirilen ifade olarak simgesini kullanarak tarafından `#if` için yönerge, ifadeyi hesaplar `true`.</span><span class="sxs-lookup"><span data-stu-id="06428-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="06428-119">Ayrıca, bir simge ile tanımlayabilirsiniz [/ define](../compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="06428-119">You can also define a symbol with the [/define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="06428-120">İle bir simge tanımlarını Kaldır [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="06428-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="06428-121">İle tanımlayan bir sembol `/define` veya `#define` aynı ada sahip bir değişken çakışan değil.</span><span class="sxs-lookup"><span data-stu-id="06428-121">A symbol that you define with `/define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="06428-122">Diğer bir deyişle, önişlemci yönergesi için bir değişken adı geçirilmemelidir ve bir simge yalnızca önişlemci yönergesi değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="06428-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="06428-123">İle oluşturulmuş bir simge kapsamını `#define` onu tanımlandığı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="06428-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="06428-124">Derleme Sistemi aynı zamanda farklı temsil eden önceden tanımlanmış önişlemci simgeleri bilmez [hedef çerçeveler](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="06428-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="06428-125">Birden fazla .NET uygulama veya sürüm hedefleyebilirsiniz uygulamaları oluştururken yararlı oldukları.</span><span class="sxs-lookup"><span data-stu-id="06428-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="06428-126">Diğer önceden tanımlanmış semboller hata ayıklama ve izleme sabitleri içerir.</span><span class="sxs-lookup"><span data-stu-id="06428-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="06428-127">Proje kullanmak için ayarlanan değerlerle geçersiz kılabilirsiniz `#define`.</span><span class="sxs-lookup"><span data-stu-id="06428-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="06428-128">Hata ayıklama simgesi, örneğin, yapı yapılandırma özelliklerini ("Hata ayıklama" veya "Yayın" modu) bağlı olarak otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="06428-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="06428-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="06428-129">Examples</span></span>

<span data-ttu-id="06428-130">Aşağıdaki örnekte bir dosyada MYTEST sembolünü tanımlayın ve MYTEST ve hata ayıklama simgeleri değerlerini test gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="06428-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="06428-131">Bu örnek çıktı projenin hata ayıklama veya yayın yapılandırma modunu olup yerleşik bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="06428-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="06428-132">Aşağıdaki örnek, mümkün olduğunda yeni API'lerini kullanabilmek için farklı bir hedef çerçeveyi test etme gösterir:</span><span class="sxs-lookup"><span data-stu-id="06428-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="06428-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06428-133">See also</span></span>

[<span data-ttu-id="06428-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="06428-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="06428-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="06428-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="06428-136">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="06428-136">C# Preprocessor Directives</span></span>](index.md)  
<span data-ttu-id="06428-137">[Nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="06428-137">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span></span>
