---
title: Yönergeler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584650"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="3c761-102">Yönergeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c761-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="3c761-103">Bu bölümdeki konular, Visual Basic kaynak kodu derleyici yönergeleri belge.</span><span class="sxs-lookup"><span data-stu-id="3c761-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c761-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c761-104">In This Section</span></span>  
 <span data-ttu-id="3c761-105">[#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md) --derleyici sabiti tanımlayın</span><span class="sxs-lookup"><span data-stu-id="3c761-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="3c761-106">[#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md) --kaynak satırları ve metin kaynağına dış arasında bir eşleme belirtmek</span><span class="sxs-lookup"><span data-stu-id="3c761-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="3c761-107">[#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --seçili kod bloklarını derleme</span><span class="sxs-lookup"><span data-stu-id="3c761-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="3c761-108">[#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md) --daraltma ve Visual Studio düzenleyicisinde kodun bölümlerini gizleme</span><span class="sxs-lookup"><span data-stu-id="3c761-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="3c761-109">**#Disable, #Enable** --devre dışı bırakın ve kod bölgeler için belirli uyarıları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3c761-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="3c761-110">Devre dışı bırakabilir ve uyarı kodlarının virgülle ayrılmış bir liste çok etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3c761-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c761-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3c761-111">Related Sections</span></span>  
 [<span data-ttu-id="3c761-112">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3c761-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="3c761-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c761-113">Visual Basic</span></span>](../../../visual-basic/index.md)
