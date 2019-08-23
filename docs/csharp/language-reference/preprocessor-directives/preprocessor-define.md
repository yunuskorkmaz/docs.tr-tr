---
title: '#C# başvuru tanımla'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: d207c96621564acd8070c9d5f618f43a6d8f15a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924597"
---
# <a name="define-c-reference"></a><span data-ttu-id="9aca6-102">#define (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9aca6-102">#define (C# Reference)</span></span>
<span data-ttu-id="9aca6-103">Bir sembol `#define` tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9aca6-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="9aca6-104">[#İf](./preprocessor-if.md) yönergesine geçirilen ifade olarak sembolünü kullandığınızda, aşağıdaki örnekte gösterildiği gibi ifade olarak değerlendirilir `true`.</span><span class="sxs-lookup"><span data-stu-id="9aca6-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="9aca6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9aca6-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9aca6-106">Yönerge `#define` , genellikle C ve C++' de yapıldığı gibi sabit değerleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="9aca6-107">İçindeki C# sabitler, bir sınıfın veya yapının statik üyeleri olarak en iyi şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9aca6-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="9aca6-108">Bu tür sabitlere sahipseniz, bunları tutmak için ayrı bir "sabitler" sınıfı oluşturmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9aca6-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="9aca6-109">Simgeler, derleme koşullarını belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9aca6-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="9aca6-110">Sembol için [#if](./preprocessor-if.md) ya da [#elif](./preprocessor-elif.md)ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="9aca6-111">Koşullu derleme gerçekleştirmek <xref:System.Diagnostics.ConditionalAttribute> için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="9aca6-112">Bir sembol tanımlayabilirsiniz, ancak bir simgeye değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9aca6-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="9aca6-113">Ayrıca Önişlemci yönergeleri olmayan herhangi bir yönergeyi kullanmadan önce yönergedosyadagörünmelidir.`#define`</span><span class="sxs-lookup"><span data-stu-id="9aca6-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="9aca6-114">Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9aca6-115">[#Undef](./preprocessor-undef.md)bir simge tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="9aca6-116">`-define` Veya ile`#define` tanımladığınız bir sembol aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="9aca6-117">Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9aca6-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="9aca6-118">Kullanılarak `#define` oluşturulan bir simgenin kapsamı, sembolün tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="9aca6-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="9aca6-119">Aşağıdaki örnekte gösterildiği gibi yönergeleri dosyanın en üstüne koymanız `#define` gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aca6-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="9aca6-120">Bir simgenin nasıl tanımlanacağını gösteren bir örnek için bkz. [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="9aca6-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aca6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aca6-121">See also</span></span>

- [<span data-ttu-id="9aca6-122">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9aca6-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9aca6-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9aca6-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9aca6-124">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9aca6-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="9aca6-125">const</span><span class="sxs-lookup"><span data-stu-id="9aca6-125">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="9aca6-126">Nasıl yapılır: Izleme ve hata ayıklama ile koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="9aca6-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="9aca6-127">#undef</span><span class="sxs-lookup"><span data-stu-id="9aca6-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="9aca6-128">#if</span><span class="sxs-lookup"><span data-stu-id="9aca6-128">#if</span></span>](./preprocessor-if.md)
