---
title: '#satır (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: f3ebecda7761e6249656e0b9f8543ae1252b844e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395143"
---
# <a name="line-c-reference"></a><span data-ttu-id="3fc1f-102">#line (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3fc1f-102">#line (C# Reference)</span></span>
<span data-ttu-id="3fc1f-103">`#line` Derleyicinin değiştirmenize olanak tanır satır numaraları ve (isteğe bağlı olarak) hataları ve uyarıları için dosya adı çıktı.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="3fc1f-104">Aşağıdaki örnek, iki uyarı satır numaraları ile ilişkili rapor gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="3fc1f-105">`#line 200` Yönergesi, sonraki satırın numarasını (varsayılan #6 olmasına rağmen) 200 olmasını zorlar ve sonraki #line yönergesi kadar dosya adı "Özel" raporlanır.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="3fc1f-106">#Line varsayılan yönergesi, önceki yönerge tarafından yeniden numaralandırılır satırları sayar kendi varsayılan numaralandırma için satır numaralandırmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;
        int j;
#line default  
        char c;
        float f;
#line hidden // numbering not affected  
        string s;   
        double d;
    }  
}  
```  
<span data-ttu-id="3fc1f-107">Derleme aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3fc1f-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="3fc1f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fc1f-108">Remarks</span></span>  
 <span data-ttu-id="3fc1f-109">`#line` Yönergesi bir derleme işlemi otomatik, ara adım modunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="3fc1f-110">Örneğin, satırları, özgün kaynak kodu dosyasından kaldırıldı, ancak derleyicinin, çıkış dosyasında numaralandırma orijinal satıra göre hala istiyordu, satırları kaldırın ve ardından özgün satır ile numaralandırma benzetimini `#line`.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="3fc1f-111">`#line hidden` Yönergesi gizler, hata ayıklayıcı art arda gelen satırlar kod Geliştirici adımlar, tüm satırlar arasında olacak şekilde bir `#line hidden` ve sonraki `#line` yönergesi (varsayarak değil başka bir `#line hidden` yönergesi) üzerinden basamaklı.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="3fc1f-112">Bu seçenek, kullanıcı tanımlı ve makine tarafından üretilen kod arasında ayırt etmek ASP.NET izin vermek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="3fc1f-113">ASP.NET bu özelliği birincil kullanıcısı olsa da, daha fazla kaynak oluşturucuları hale getirecek bunu kullanmaya olasıdır.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="3fc1f-114">A `#line hidden` yönergesi dosya adları etkilemez veya satır numaraları hatası raporlama.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="3fc1f-115">Diğer bir deyişle, gizli bir bloğu içinde bir hatayla karşılaşılırsa, derleyici geçerli dosya adı ve satır sayısı hata rapor eder.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="3fc1f-116">`#line filename` Yönergesi derleyici çıktısında görüntülenmesini istediğiniz dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="3fc1f-117">Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="3fc1f-118">Dosya adı çift tırnak içinde olmalıdır ("") ve satır numarasıyla gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="3fc1f-119">Bir kaynak kodu dosyası herhangi bir sayıda olabilir `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-119">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="3fc1f-120">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="3fc1f-120">Example 1</span></span>  
 <span data-ttu-id="3fc1f-121">Aşağıdaki örnek, hata ayıklayıcı gizli kod satırları nasıl yoksayar gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="3fc1f-122">Örneği çalıştırdığınızda, üç metin satırlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="3fc1f-123">Ancak, örnekte gösterildiği gibi bir kesme noktası ayarlayın ve kodunuz içinde adım adım F10 isabet, hata ayıklayıcı'nın gizli çizgi yok sayar göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="3fc1f-124">Ayrıca gizli satırında bir kesme noktası ayarlasanız bile hata ayıklayıcı hala yok, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3fc1f-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fc1f-125">See Also</span></span>

- [<span data-ttu-id="3fc1f-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3fc1f-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3fc1f-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3fc1f-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3fc1f-128">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3fc1f-128">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
