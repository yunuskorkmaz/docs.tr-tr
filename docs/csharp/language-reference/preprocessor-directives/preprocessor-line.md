---
title: '#satır (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 08ba94ec3f1799f858e098bd2c0e059b7f45af2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289275"
---
# <a name="line-c-reference"></a><span data-ttu-id="bf67c-102">#line (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bf67c-102">#line (C# Reference)</span></span>
<span data-ttu-id="bf67c-103">`#line` Derleyicinin satır numarasını ve (isteğe bağlı) hataları ve uyarıları için dosya adı çıktı değiştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bf67c-103">`#line` lets you modify the compiler's line number and (optionally) the file name output for errors and warnings.</span></span> <span data-ttu-id="bf67c-104">Bu örnekte, iki uyarıları satır numaralarını ile ilişkili rapor gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-104">This example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="bf67c-105">`#line 200` Yönergesi zorlar (varsayılan #7 olmasına rağmen) 200 satır numarasını ve sonraki #line yönergesi kadar dosya adı "Özel" olarak raporlanır.</span><span class="sxs-lookup"><span data-stu-id="bf67c-105">The `#line 200` directive forces the line number to be 200 (although the default is #7) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="bf67c-106">#Line varsayılan yönergesi önceki yönergesi tarafından yeniden numaralandırılır satırları sayar kendi varsayılan numaralandırma için numaralandırma satır döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf67c-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="bf67c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf67c-107">Remarks</span></span>  
 <span data-ttu-id="bf67c-108">`#line` Yönergesi derleme sürecindeki otomatik, Ara bir adımda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-108">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="bf67c-109">Örneğin, satırları özgün kaynak kodu dosyasından kaldırıldı, ancak hala özgün satır dosyasında numaralandırmasını göre çıktı üretmek için derleyici istedi, size satırları kaldırın ve özgün satır ile numaralandırma benzetimini `#line`.</span><span class="sxs-lookup"><span data-stu-id="bf67c-109">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="bf67c-110">`#line hidden` Yönergesi gizler hata ayıklayıcı art arda gelen satırlardan sağlayacak şekilde Geliştirici koduyla adımlar, tüm satırları arasında bir `#line hidden` ve sonraki `#line` yönergesi (varsayılarak olmayan başka bir `#line hidden` yönergesi) üzerinden adım adım.</span><span class="sxs-lookup"><span data-stu-id="bf67c-110">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="bf67c-111">Bu seçenek, kullanıcı tanımlı ve makine oluşturulan kod arasında ayırt etmek ASP.NET izin vermek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-111">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="bf67c-112">ASP.NET bu özelliğin birincil tüketici olsa da, daha fazla kaynak oluşturucuları yapacak bunu kullanmak olasıdır.</span><span class="sxs-lookup"><span data-stu-id="bf67c-112">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="bf67c-113">A `#line hidden` yönergesi dosya adlarını etkilemez veya satır numaraları hata raporlama.</span><span class="sxs-lookup"><span data-stu-id="bf67c-113">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="bf67c-114">Diğer bir deyişle, gizli bir bloğunda hatayla karşılaşılırsa, derleyici geçerli dosya adı ve satır numarası hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-114">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="bf67c-115">`#line filename` Yönergesi derleyici çıktısında görüntülenmesini istediğiniz dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-115">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="bf67c-116">Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf67c-116">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="bf67c-117">Dosya adı çift tırnak işaretleri içinde olmalıdır ("") ve bir satır sayısı tarafından gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-117">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="bf67c-118">Kaynak kodu dosyasının herhangi bir sayıda olabilir `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="bf67c-118">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="bf67c-119">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="bf67c-119">Example 1</span></span>  
 <span data-ttu-id="bf67c-120">Aşağıdaki örnek kodda gizli satırlar hata ayıklayıcı nasıl yoksayar gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf67c-120">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="bf67c-121">Örnek çalıştırdığınızda, üç satırlık metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf67c-121">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="bf67c-122">Ancak, örnekte gösterildiği gibi bir kesme noktası ayarlayın ve kod üzerinden adım F10 isabet zaman hata ayıklayıcı gizli çizgi yoksayar fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="bf67c-122">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="bf67c-123">Ayrıca gizli satırında bir kesme noktası ayarlasanız bile hata ayıklayıcı hala bunu göz ardı eder dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bf67c-123">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf67c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf67c-124">See Also</span></span>  
 [<span data-ttu-id="bf67c-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bf67c-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bf67c-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bf67c-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bf67c-127">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bf67c-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
