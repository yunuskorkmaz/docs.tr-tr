---
title: "Yönergeler (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a><span data-ttu-id="21c67-102">Yönergeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21c67-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="21c67-103">Bu bölümdeki konular, Visual Basic kaynak kodu derleyici yönergeleri belge.</span><span class="sxs-lookup"><span data-stu-id="21c67-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21c67-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="21c67-104">In This Section</span></span>  
 <span data-ttu-id="21c67-105">[#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md) --derleyici sabiti tanımlayın</span><span class="sxs-lookup"><span data-stu-id="21c67-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="21c67-106">[#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md) --kaynak satırları ve metin kaynağına dış arasında bir eşleme belirtmek</span><span class="sxs-lookup"><span data-stu-id="21c67-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="21c67-107">[#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --seçili kod bloklarını derleme</span><span class="sxs-lookup"><span data-stu-id="21c67-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="21c67-108">[#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md) --daraltma ve Visual Studio düzenleyicisinde kodun bölümlerini gizleme</span><span class="sxs-lookup"><span data-stu-id="21c67-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="21c67-109">**#Disable, #Enable** --devre dışı bırakın ve kod bölgeler için belirli uyarıları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="21c67-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="21c67-110">Devre dışı bırakabilir ve uyarı kodlarının virgülle ayrılmış bir liste çok etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="21c67-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="21c67-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="21c67-111">Related Sections</span></span>  
 [<span data-ttu-id="21c67-112">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="21c67-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="21c67-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c67-113">Visual Basic</span></span>](../../../visual-basic/index.md)
