---
description: 'Daha fazla bilgi edinin: #Region yönergesi'
title: '#Region Yönergesi'
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
ms.openlocfilehash: 4ba1645cfc51a69d39e6a60b5ea236dd65883e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797230"
---
# <a name="region-directive"></a><span data-ttu-id="9c0cf-103">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="9c0cf-103">#Region Directive</span></span>

<span data-ttu-id="9c0cf-104">Visual Basic dosyalardaki kod bölümlerini daraltır ve gizler.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-104">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c0cf-105">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="9c0cf-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9c0cf-106">Parts</span></span>  
  
|<span data-ttu-id="9c0cf-107">Süre</span><span class="sxs-lookup"><span data-stu-id="9c0cf-107">Term</span></span>|<span data-ttu-id="9c0cf-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="9c0cf-108">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="9c0cf-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-109">Required.</span></span> <span data-ttu-id="9c0cf-110">Daraltılan bir bölgenin başlığı olarak davranan dize.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-110">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="9c0cf-111">Bölgeler varsayılan olarak daraltılır.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-111">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="9c0cf-112">Bloğu sonlandırır `#Region` .</span><span class="sxs-lookup"><span data-stu-id="9c0cf-112">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c0cf-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c0cf-113">Remarks</span></span>  

 <span data-ttu-id="9c0cf-114">`#Region`Visual Studio Code düzenleyicisinin ana hat özelliğini kullanırken genişletilecek veya daraltılacak bir kod bloğu belirtmek için yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-114">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="9c0cf-115">Benzer bölgeleri gruplamak için diğer bölgelere bölge yerleştirebilir veya *iç içe* geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-115">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0cf-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c0cf-116">Example</span></span>  

 <span data-ttu-id="9c0cf-117">Bu örnek, `#Region` yönergesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-117">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9c0cf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c0cf-118">See also</span></span>

- [<span data-ttu-id="9c0cf-119">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="9c0cf-119">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="9c0cf-120">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c0cf-120">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="9c0cf-121">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="9c0cf-121">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
