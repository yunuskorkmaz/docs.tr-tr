---
title: "#<a name=\"if-c-reference\"></a>varsa (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a><span data-ttu-id="341a8-102">#if (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="341a8-102">#if (C# Reference)</span></span>
<span data-ttu-id="341a8-103">C# Derleyici karşılaştığında bir `#if` yönergesi, ardından sonunda göre bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) yalnızca belirtilen simgeyi tanımlanırsa yönerge, bu kod yönergeleri arasında derlenir.</span><span class="sxs-lookup"><span data-stu-id="341a8-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="341a8-104">C ve C++ aksine, bir simgeye sayısal bir değer atayamazsınız; C# #if ifade Boolean ve yalnızca simgenin veya tanımlanmış olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="341a8-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="341a8-105">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="341a8-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="341a8-106">İşleçleri kullanabilirsiniz [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) (eşitlik) [! =](../../../csharp/language-reference/operators/not-equal-operator.md) (yalnızca sınamak için eşitsizlik) [true](../../../csharp/language-reference/keywords/true.md) veya [false](../../../csharp/language-reference/keywords/false.md) .</span><span class="sxs-lookup"><span data-stu-id="341a8-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="341a8-107">TRUE simgenin tanımlanan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="341a8-107">True means the symbol is defined.</span></span> <span data-ttu-id="341a8-108">Deyim `#if DEBUG` aynı anlamı taşır `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="341a8-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="341a8-109">İşleçleri kullanabilirsiniz [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) (ve) [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (veya) ve [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="341a8-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="341a8-110">(birden çok simgeleri tanımlı olup olmadığını değerlendirmek için değil).</span><span class="sxs-lookup"><span data-stu-id="341a8-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="341a8-111">Ayrıca, simgeler ve parantez işleçlerle de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="341a8-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="341a8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="341a8-112">Remarks</span></span>  
 <span data-ttu-id="341a8-113">`#if`, birlikte [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), ve [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) yönergeleri sağlar içerebilir veya bir veya daha fazla simgeleri varlığını göre kod dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="341a8-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="341a8-114">Hata ayıklama derlemesi kodunu derlerken veya belirli bir yapılandırma için derleme sırasında bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="341a8-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="341a8-115">Koşullu bir yönerge başlayarak bir `#if` yönergesi açıkça bitirilmelidir ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="341a8-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="341a8-116">`#define`ifade olarak simgesi kullanarak geçirilecek şekilde bir simge tanımlamanıza olanak tanır `#if` ifade için yönerge, değerlendirecek `true`.</span><span class="sxs-lookup"><span data-stu-id="341a8-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="341a8-117">Ayrıca, bir simge ile tanımlayabilirsiniz [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="341a8-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="341a8-118">İle bir simge tanımlarını Kaldır [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="341a8-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="341a8-119">İle tanımlayan bir sembol `/define` veya `#define` aynı ada sahip bir değişken çakışmayan.</span><span class="sxs-lookup"><span data-stu-id="341a8-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="341a8-120">Diğer bir deyişle, önişlemci yönergesi için bir değişken adı geçirilmemelidir ve bir simge yalnızca önişlemci yönergesi değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="341a8-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="341a8-121">İle oluşturulmuş bir simge kapsamını `#define` onu tanımlandığı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="341a8-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="341a8-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="341a8-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
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
  
 <span data-ttu-id="341a8-123">**Hata ayıklama ve MYTEST tanımlanır**</span><span class="sxs-lookup"><span data-stu-id="341a8-123">**DEBUG and MYTEST are defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="341a8-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="341a8-124">See Also</span></span>  
 [<span data-ttu-id="341a8-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="341a8-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="341a8-126">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="341a8-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="341a8-127">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="341a8-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
