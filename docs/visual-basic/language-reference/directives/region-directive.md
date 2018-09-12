---
title: '#Bölge yönergesi (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 204b53751fce4f9a3e038ae7c44634522d54657c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707522"
---
# <a name="region-directive"></a><span data-ttu-id="3788f-102">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="3788f-102">#Region Directive</span></span>
<span data-ttu-id="3788f-103">Daraltır ve Visual Basic dosyalarında kod bölümlerini gizler.</span><span class="sxs-lookup"><span data-stu-id="3788f-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3788f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3788f-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="3788f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3788f-105">Parts</span></span>  
  
|<span data-ttu-id="3788f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="3788f-106">Term</span></span>|<span data-ttu-id="3788f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="3788f-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="3788f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3788f-108">Required.</span></span> <span data-ttu-id="3788f-109">Bunu daraltıldığında bir bölge başlığı olarak davranan dize.</span><span class="sxs-lookup"><span data-stu-id="3788f-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="3788f-110">Bölgeleri varsayılan olarak daraltılır.</span><span class="sxs-lookup"><span data-stu-id="3788f-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="3788f-111">Sonlandırır `#Region` blok.</span><span class="sxs-lookup"><span data-stu-id="3788f-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3788f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3788f-112">Remarks</span></span>  
 <span data-ttu-id="3788f-113">Kullanım `#Region` genişletmek veya daraltmak için anahat oluşturma özelliği Visual Studio Kod Düzenleyicisi'nin kullanırken kod bloğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3788f-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="3788f-114">Yerleştirebilirsiniz veya *iç içe*, benzer bölgeleri gruplamak için başka bölgelerde bulunan bölge.</span><span class="sxs-lookup"><span data-stu-id="3788f-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3788f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="3788f-115">Example</span></span>  
 <span data-ttu-id="3788f-116">Bu örnekte `#Region` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="3788f-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3788f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3788f-117">See Also</span></span>  
 [<span data-ttu-id="3788f-118">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="3788f-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="3788f-119">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3788f-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="3788f-120">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="3788f-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
