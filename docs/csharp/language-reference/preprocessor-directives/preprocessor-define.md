---
title: '#(C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 1903b96de5f9dfa4efc252897a4a4bd18ed64924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286740"
---
# <a name="define-c-reference"></a><span data-ttu-id="c5bd8-102">#define (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c5bd8-102">#define (C# Reference)</span></span>
<span data-ttu-id="c5bd8-103">Kullandığınız `#define` bir simge tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="c5bd8-104">Geçirilen ifade olarak simgenin kullandığınızda [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ifade için yönerge, değerlendirecek `true`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c5bd8-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="c5bd8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5bd8-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5bd8-106">`#define` Yönergesi, genellikle C ve C++ gerçekleştirilir gibi sabit değerleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="c5bd8-107">C# sabitleri en iyi sınıfta veya yapı statik üyeleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="c5bd8-108">Bu tür birkaç sabitleri varsa, bunları tutmak için ayrı bir "Sabitleri" sınıf oluşturmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="c5bd8-109">Simgeler, derleme için koşulları belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="c5bd8-110">Ya da simgesiyle için test edebilirsiniz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="c5bd8-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="c5bd8-111">Aynı zamanda `conditional` koşullu derleme gerçekleştirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="c5bd8-112">Bir simge tanımlayabilirsiniz, ancak bir sembol için bir değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="c5bd8-113">`#define` Yönergesi de önişlemci yönergeleri olmayan herhangi bir yönerge kullanmadan önce dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="c5bd8-114">Ayrıca, bir simge ile tanımlayabilirsiniz [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-114">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c5bd8-115">İle bir simge tanımlarını Kaldır [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="c5bd8-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="c5bd8-116">İle tanımlayan bir sembol `/define` veya `#define` aynı ada sahip bir değişken çakışmayan.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-116">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="c5bd8-117">Diğer bir deyişle, önişlemci yönergesi için bir değişken adı geçirilmemelidir ve bir simge yalnızca önişlemci yönergesi değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="c5bd8-118">Kullanılarak oluşturulmuş bir simge kapsamını `#define` simgenin tanımlanmıştı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="c5bd8-119">Aşağıdaki örnekte gösterildiği gibi konulmalıdır `#define` dosyanın üst kısmındaki yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="c5bd8-120">Bir simge tanımlarını Kaldır konusunda bir örnek için bkz: [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="c5bd8-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bd8-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5bd8-121">See Also</span></span>  
 [<span data-ttu-id="c5bd8-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5bd8-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5bd8-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c5bd8-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5bd8-124">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c5bd8-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="c5bd8-125">const</span><span class="sxs-lookup"><span data-stu-id="c5bd8-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="c5bd8-126">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="c5bd8-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="c5bd8-127">#undef</span><span class="sxs-lookup"><span data-stu-id="c5bd8-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="c5bd8-128">#if</span><span class="sxs-lookup"><span data-stu-id="c5bd8-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
