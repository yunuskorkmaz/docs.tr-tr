---
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
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409952"
---
# <a name="region-directive"></a><span data-ttu-id="ec1d2-102">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="ec1d2-102">#Region Directive</span></span>

<span data-ttu-id="ec1d2-103">Visual Basic dosyalardaki kod bölümlerini daraltır ve gizler.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec1d2-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="ec1d2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ec1d2-105">Parts</span></span>  
  
|<span data-ttu-id="ec1d2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ec1d2-106">Term</span></span>|<span data-ttu-id="ec1d2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ec1d2-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="ec1d2-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-108">Required.</span></span> <span data-ttu-id="ec1d2-109">Daraltılan bir bölgenin başlığı olarak davranan dize.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="ec1d2-110">Bölgeler varsayılan olarak daraltılır.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="ec1d2-111">Bloğu sonlandırır `#Region` .</span><span class="sxs-lookup"><span data-stu-id="ec1d2-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec1d2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec1d2-112">Remarks</span></span>  

 <span data-ttu-id="ec1d2-113">`#Region`Visual Studio Code düzenleyicisinin ana hat özelliğini kullanırken genişletilecek veya daraltılacak bir kod bloğu belirtmek için yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="ec1d2-114">Benzer bölgeleri gruplamak için diğer bölgelere bölge yerleştirebilir veya *iç içe*geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec1d2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec1d2-115">Example</span></span>  

 <span data-ttu-id="ec1d2-116">Bu örnek, `#Region` yönergesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ec1d2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec1d2-117">See also</span></span>

- [<span data-ttu-id="ec1d2-118">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="ec1d2-118">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="ec1d2-119">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec1d2-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="ec1d2-120">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="ec1d2-120">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
