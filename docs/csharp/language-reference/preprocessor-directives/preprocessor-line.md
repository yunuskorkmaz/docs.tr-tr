---
title: '#satır C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608531"
---
# <a name="line-c-reference"></a><span data-ttu-id="6717d-102">#line (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6717d-102">#line (C# Reference)</span></span>

<span data-ttu-id="6717d-103">`#line`Derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) hata ve uyarı için dosya adı çıktısını değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="6717d-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="6717d-104">Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6717d-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="6717d-105">Yönerge, sonraki satırın numarasını 200 (varsayılan değer #6) olarak zorlar ve sonraki `#line` yönergeye kadar dosya adı "özel" olarak raporlanır. `#line 200`</span><span class="sxs-lookup"><span data-stu-id="6717d-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="6717d-106">`#line default` Yönerge, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmayla satır numaralandırmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="6717d-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

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

<span data-ttu-id="6717d-107">Derleme aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6717d-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="6717d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6717d-108">Remarks</span></span>

<span data-ttu-id="6717d-109">`#line` Yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6717d-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="6717d-110">Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından özgün satır numaralandırmasının `#line`benzetimini yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6717d-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="6717d-111">Yönerge, hata ayıklayıcıdan ardışık satırları gizler, örneğin, Geliştirici kod içinde, bir ve `#line` sonraki yönerge arasındaki herhangi bir `#line hidden` satır (başka bir `#line hidden` yönerge olmadığı varsayılarak) `#line hidden` ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="6717d-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="6717d-112">Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6717d-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="6717d-113">ASP.NET bu özelliğin birincil tüketicisi olsa da, büyük olasılıkla daha fazla kaynak oluşturanlar bunu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="6717d-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="6717d-114">Bir `#line hidden` yönerge, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="6717d-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="6717d-115">Diğer bir deyişle, gizli bir blokta bir hata ile karşılaşılırsa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6717d-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="6717d-116">`#line filename` Yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6717d-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="6717d-117">Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6717d-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="6717d-118">Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="6717d-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="6717d-119">Kaynak kodu dosyası herhangi bir sayıda `#line` yönergeler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6717d-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="6717d-120">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="6717d-120">Example 1</span></span>

<span data-ttu-id="6717d-121">Aşağıdaki örnek, hata ayıklayıcının koddaki gizli satırları nasıl yoksaydığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6717d-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="6717d-122">Örneği çalıştırdığınızda üç satırlık metin görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6717d-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="6717d-123">Ancak, örnekte gösterildiği gibi bir kesme noktası ayarladığınızda ve kodun içinde ilerlemek için F10 'e bastığınızda, hata ayıklayıcının gizli çizgiyi yoksaydığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6717d-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="6717d-124">Ayrıca, gizli satırda bir kesme noktası ayarlasanız bile hata ayıklayıcının yok saymaya devam ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6717d-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6717d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6717d-125">See also</span></span>

- [<span data-ttu-id="6717d-126">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6717d-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6717d-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6717d-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6717d-128">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6717d-128">C# Preprocessor Directives</span></span>](./index.md)
