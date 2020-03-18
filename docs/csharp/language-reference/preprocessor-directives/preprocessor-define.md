---
title: '#define - C# Referans'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173438"
---
# <a name="define-c-reference"></a><span data-ttu-id="b0d9a-102">#define (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0d9a-102">#define (C# Reference)</span></span>
<span data-ttu-id="b0d9a-103">Bir `#define` sembol tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="b0d9a-104">Sembolü [#if](./preprocessor-if.md) yönergesine geçirilen ifade olarak kullandığınızda, ifade `true`aşağıdaki örnekte görüldüğü gibi aşağıdaki leri değerlendirecektir:</span><span class="sxs-lookup"><span data-stu-id="b0d9a-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="b0d9a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0d9a-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0d9a-106">Yönerge, `#define` c ve c++'da genellikle yapıldığı gibi sabit değerleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="b0d9a-107">C#'daki sabitler en iyi sınıfın veya yapının statik üyeleri olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="b0d9a-108">Bu tür birkaç sabitinvarsa, bunları tutmak için ayrı bir "Sabitler" sınıfı oluşturmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="b0d9a-109">Semboller derleme için koşulları belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="b0d9a-110">#if [veya](./preprocessor-if.md) [#elif](./preprocessor-elif.md)ile sembol için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="b0d9a-111">Koşullu derleme <xref:System.Diagnostics.ConditionalAttribute> gerçekleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="b0d9a-112">Bir simge tanımlayabilirsiniz, ancak bir sembole değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="b0d9a-113">Önişlemci `#define` yönergeleri olmayan yönergeleri kullanmadan önce yönerge nin dosyada görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="b0d9a-114">[-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir sembol de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b0d9a-115">Bir sembolü [#undef](./preprocessor-undef.md)ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="b0d9a-116">Tanımladığınız `-define` veya tanımladığınız `#define` bir sembol, aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="b0d9a-117">Diğer bir diğer adıyla, bir değişken adı bir önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir önişlemci yönergesi tarafından değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="b0d9a-118">Kullanılarak `#define` oluşturulan bir sembolün kapsamı, sembolün tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="b0d9a-119">Aşağıdaki örnekte de görüldüğü `#define` gibi, yönergeleri dosyanın en üstüne koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="b0d9a-120">Bir sembolün nasıl tanımlanabildiğini anlatan bir örnek için bkz. [#undef.](./preprocessor-undef.md)</span><span class="sxs-lookup"><span data-stu-id="b0d9a-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d9a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0d9a-121">See also</span></span>

- [<span data-ttu-id="b0d9a-122">C# Referans</span><span class="sxs-lookup"><span data-stu-id="b0d9a-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0d9a-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0d9a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0d9a-124">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="b0d9a-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="b0d9a-125">const</span><span class="sxs-lookup"><span data-stu-id="b0d9a-125">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="b0d9a-126">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="b0d9a-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="b0d9a-127">#undef</span><span class="sxs-lookup"><span data-stu-id="b0d9a-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="b0d9a-128">#if</span><span class="sxs-lookup"><span data-stu-id="b0d9a-128">#if</span></span>](./preprocessor-if.md)
