---
description: '#tanımlama-C# başvurusu'
title: '#tanımlama-C# başvurusu'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 961c20c091a4a6d7da421d94500abd41d2d60a5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160508"
---
# <a name="define-c-reference"></a><span data-ttu-id="f19c9-103">#define (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f19c9-103">#define (C# Reference)</span></span>

<span data-ttu-id="f19c9-104">`#define`Bir sembol tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f19c9-104">You use `#define` to define a symbol.</span></span> <span data-ttu-id="f19c9-105">[#İf](./preprocessor-if.md) yönergesine geçirilen ifade olarak sembolünü kullandığınızda, `true` Aşağıdaki örnekte gösterildiği gibi ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f19c9-105">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="f19c9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f19c9-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f19c9-107">`#define`Yönerge, genellikle C ve C++ ' da yapıldığı gibi sabit değerleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="f19c9-108">C# ' deki sabitler, bir sınıfın veya yapının statik üyeleri olarak en iyi şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f19c9-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="f19c9-109">Bu tür sabitlere sahipseniz, bunları tutmak için ayrı bir "sabitler" sınıfı oluşturmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f19c9-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="f19c9-110">Simgeler, derleme koşullarını belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f19c9-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="f19c9-111">Sembol için [#if](./preprocessor-if.md) ya da [#elif](./preprocessor-elif.md)ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-111">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="f19c9-112"><xref:System.Diagnostics.ConditionalAttribute>Koşullu derleme gerçekleştirmek için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-112">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="f19c9-113">Bir sembol tanımlayabilirsiniz, ancak bir simgeye değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f19c9-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="f19c9-114">`#define`Ayrıca Önişlemci yönergeleri olmayan herhangi bir yönergeyi kullanmadan önce yönerge dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="f19c9-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="f19c9-115">Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-115">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f19c9-116">[#Undef](./preprocessor-undef.md)bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-116">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="f19c9-117">Veya ile tanımladığınız bir sembol `-define` `#define` aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-117">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="f19c9-118">Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f19c9-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="f19c9-119">Kullanılarak oluşturulan bir simgenin kapsamı, `#define` sembolün tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="f19c9-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="f19c9-120">Aşağıdaki örnekte gösterildiği gibi `#define` yönergeleri dosyanın en üstüne koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f19c9-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="f19c9-121">Bir simgenin nasıl tanımlanacağını gösteren bir örnek için bkz. [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="f19c9-121">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19c9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f19c9-122">See also</span></span>

- [<span data-ttu-id="f19c9-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f19c9-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f19c9-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f19c9-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f19c9-125">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f19c9-125">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="f19c9-126">const</span><span class="sxs-lookup"><span data-stu-id="f19c9-126">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="f19c9-127">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="f19c9-127">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="f19c9-128">#undef</span><span class="sxs-lookup"><span data-stu-id="f19c9-128">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="f19c9-129">#if</span><span class="sxs-lookup"><span data-stu-id="f19c9-129">#if</span></span>](./preprocessor-if.md)
