---
title: Yönergeler
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410003"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="06ddd-102">Yönergeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ddd-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="06ddd-103">Bu bölümdeki konular Visual Basic kaynak kodu derleyici yönergelerini belgeleyin.</span><span class="sxs-lookup"><span data-stu-id="06ddd-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06ddd-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="06ddd-104">In This Section</span></span>  

 <span data-ttu-id="06ddd-105">[#Const Yönergesi](const-directive.md) --derleyici sabiti tanımlama</span><span class="sxs-lookup"><span data-stu-id="06ddd-105">[#Const Directive](const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="06ddd-106">[#ExternalSource yönergesi](externalsource-directive.md) --kaynak satırları ile kaynağın harici metni arasında bir eşleme belirtin</span><span class="sxs-lookup"><span data-stu-id="06ddd-106">[#ExternalSource Directive](externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="06ddd-107">[#If... Sonra... #Else yönergeleri](if-then-else-directives.md) --seçili kod bloklarını derle</span><span class="sxs-lookup"><span data-stu-id="06ddd-107">[#If...Then...#Else Directives](if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="06ddd-108">[#Region yönergesi](region-directive.md) --Visual Studio düzenleyicisinde kodun bölümlerini daraltma ve gizleme</span><span class="sxs-lookup"><span data-stu-id="06ddd-108">[#Region Directive](region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="06ddd-109">**#Disable, #Enable** --kod bölgeleri için belirli uyarıları devre dışı bırakın ve etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="06ddd-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="06ddd-110">Virgülle ayrılmış bir uyarı kodları listesini devre dışı bırakabilir ve etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06ddd-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06ddd-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="06ddd-111">Related Sections</span></span>  

 [<span data-ttu-id="06ddd-112">Visual Basic dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="06ddd-112">Visual Basic Language Reference</span></span>](../index.md)  
  