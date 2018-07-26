---
title: '#tanımlama (C# Başvurusu)'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: f40c32a89641256e4f8fe30cd24f523b898139d5
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143485"
---
# <a name="define-c-reference"></a><span data-ttu-id="c3899-102">#define (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c3899-102">#define (C# Reference)</span></span>
<span data-ttu-id="c3899-103">Kullandığınız `#define` simge tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="c3899-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="c3899-104">Geçirilen ifade olarak sembol kullanırken [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi, ifade için değerlendirilecek olan `true`aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c3899-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="c3899-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3899-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3899-106">`#define` Yönergesi, genellikle C ve C++ içinde olduğu gibi sabit değerler bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c3899-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="c3899-107">C# içinde sabitleri en iyi bir sınıfın veya yapının üyeleri statik olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c3899-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="c3899-108">Birkaç sabitiniz varsa, bunları tutmak için ayrı bir "Sabitler" sınıfı oluşturmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c3899-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="c3899-109">Derleme koşullarını belirtmek için simgeler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3899-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="c3899-110">Sembolü ile ya da test [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="c3899-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="c3899-111">Ayrıca `conditional` koşullu derleme gerçekleştirmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c3899-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="c3899-112">Bir simge tanımlayabilir ancak bir simgeye değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c3899-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="c3899-113">`#define` Önişlemci yönergesi de olmayan yönergeleri kullanmadan önce yönergesinin dosyada görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3899-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="c3899-114">Ayrıca bir simge tanımlayabilirsiniz [-tanımlama](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c3899-114">You can also define a symbol with the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c3899-115">Sahip bir simge tanımlarını Kaldır [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="c3899-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="c3899-116">İle tanımladığınız bir sembol `-define` veya `#define` aynı ada sahip bir değişkenle çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="c3899-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="c3899-117">Diğer bir deyişle, bir değişken adı bir önişlemci yönergesine geçmemiş olmalıdır ve bir simge yalnızca bir önişlemci yönergesince değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c3899-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="c3899-118">Kullanılarak oluşturulan bir simgenin kapsamı `#define` simgenin tanımlandığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="c3899-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="c3899-119">Aşağıdaki örnekte gösterildiği gibi yerleştirmelisiniz `#define` yönergelerini dosyanın üst.</span><span class="sxs-lookup"><span data-stu-id="c3899-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="c3899-120">Bir sembolün tanımını kaldırmaya ilişkin bir örnek için bkz. [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="c3899-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3899-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3899-121">See Also</span></span>  
 [<span data-ttu-id="c3899-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c3899-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c3899-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c3899-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c3899-124">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c3899-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="c3899-125">const</span><span class="sxs-lookup"><span data-stu-id="c3899-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="c3899-126">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="c3899-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="c3899-127">#undef</span><span class="sxs-lookup"><span data-stu-id="c3899-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="c3899-128">#if</span><span class="sxs-lookup"><span data-stu-id="c3899-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
