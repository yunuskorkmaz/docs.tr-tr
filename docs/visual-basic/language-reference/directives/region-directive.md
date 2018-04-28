---
title: '#Bölge yönergesi'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83ceac7d73eff23e16c5f6efb1c4eb8a2210ee2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="region-directive"></a><span data-ttu-id="f31ea-102">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f31ea-102">#Region Directive</span></span>
<span data-ttu-id="f31ea-103">Daraltır ve Visual Basic dosyaları kodda bölümlerini gizler.</span><span class="sxs-lookup"><span data-stu-id="f31ea-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f31ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f31ea-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="f31ea-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f31ea-105">Parts</span></span>  
  
|<span data-ttu-id="f31ea-106">Terim</span><span class="sxs-lookup"><span data-stu-id="f31ea-106">Term</span></span>|<span data-ttu-id="f31ea-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="f31ea-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="f31ea-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f31ea-108">Required.</span></span> <span data-ttu-id="f31ea-109">Daraltılmış durumda olduğunda, bir bölge başlığı olarak davranan dizesi.</span><span class="sxs-lookup"><span data-stu-id="f31ea-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="f31ea-110">Bölgeleri varsayılan olarak daraltılır.</span><span class="sxs-lookup"><span data-stu-id="f31ea-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="f31ea-111">Sonlandırır `#Region` bloğu.</span><span class="sxs-lookup"><span data-stu-id="f31ea-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f31ea-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f31ea-112">Remarks</span></span>  
 <span data-ttu-id="f31ea-113">Kullanım `#Region` yönergesi genişletmek veya Visual Studio Kod Düzenleyicisi'nin anahat özelliğini kullanırken daraltmak için kod bloğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="f31ea-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="f31ea-114">Koyabilirsiniz, veya *iç içe*, bölge benzer bölgeler gruplamak için diğer bölge içinde.</span><span class="sxs-lookup"><span data-stu-id="f31ea-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f31ea-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f31ea-115">Example</span></span>  
 <span data-ttu-id="f31ea-116">Bu örnekte `#Region` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="f31ea-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f31ea-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f31ea-117">See Also</span></span>  
 [<span data-ttu-id="f31ea-118">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f31ea-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="f31ea-119">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f31ea-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="f31ea-120">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="f31ea-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
