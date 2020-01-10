---
title: '#satır C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712500"
---
# <a name="line-c-reference"></a><span data-ttu-id="256ab-102">#line (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="256ab-102">#line (C# Reference)</span></span>

<span data-ttu-id="256ab-103">`#line`, derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) dosya adı çıktısını hatalar ve uyarılar için değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="256ab-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="256ab-104">Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="256ab-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="256ab-105">`#line 200` yönergesi sonraki satırın numarasını 200 olarak zorlar (varsayılan değer #6 olur) ve sonraki `#line` yönergesine kadar dosya adı "özel" olarak raporlanır.</span><span class="sxs-lookup"><span data-stu-id="256ab-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="256ab-106">`#line default` yönergesi, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmaya satır numaralandırmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="256ab-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

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

<span data-ttu-id="256ab-107">Derleme aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="256ab-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="256ab-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="256ab-108">Remarks</span></span>

<span data-ttu-id="256ab-109">`#line` yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="256ab-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="256ab-110">Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından `#line`orijinal satır numaralandırmasının benzetimini yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="256ab-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="256ab-111">`#line hidden` yönergesi, hata ayıklayıcıdan ardışık satırları gizler, örneğin, geliştirici kodda, bir `#line hidden` ve bir sonraki `#line` yönergesi arasındaki herhangi bir satır (başka bir `#line hidden` yönergesi olmadığı varsayılırsa), bu yana bir adım daha alınır.</span><span class="sxs-lookup"><span data-stu-id="256ab-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="256ab-112">Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="256ab-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="256ab-113">ASP.NET bu özelliğin birincil tüketicisi olsa da, büyük olasılıkla daha fazla kaynak oluşturanlar bunu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="256ab-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="256ab-114">`#line hidden` yönergesi, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="256ab-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="256ab-115">Diğer bir deyişle, gizli bir blokta bir hata ile karşılaşılırsa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="256ab-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="256ab-116">`#line filename` yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="256ab-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="256ab-117">Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="256ab-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="256ab-118">Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="256ab-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="256ab-119">Kaynak kodu dosyasında herhangi bir sayıda `#line` yönergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="256ab-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="256ab-120">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="256ab-120">Example 1</span></span>

<span data-ttu-id="256ab-121">Aşağıdaki örnek, hata ayıklayıcının koddaki gizli satırları nasıl yoksaydığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="256ab-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="256ab-122">Örneği çalıştırdığınızda üç satırlık metin görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="256ab-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="256ab-123">Ancak, örnekte gösterildiği gibi bir kesme noktası ayarladığınızda ve kodun içinde ilerlemek için F10 'e bastığınızda, hata ayıklayıcının gizli çizgiyi yoksaydığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="256ab-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="256ab-124">Ayrıca, gizli satırda bir kesme noktası ayarlasanız bile hata ayıklayıcının yok saymaya devam ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="256ab-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="256ab-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="256ab-125">See also</span></span>

- [<span data-ttu-id="256ab-126">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="256ab-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="256ab-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="256ab-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="256ab-128">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="256ab-128">C# Preprocessor Directives</span></span>](./index.md)
