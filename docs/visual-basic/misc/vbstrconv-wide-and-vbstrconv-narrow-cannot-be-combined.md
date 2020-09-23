---
title: VbStrConv. Wide ve VbStrConv. dar birleştirilemez
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: 7193d1f635ff877ab5d07f03584f19f5ce18138a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059374"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a><span data-ttu-id="0b5f6-102">VbStrConv. Wide ve VbStrConv. dar birleştirilemez</span><span class="sxs-lookup"><span data-stu-id="0b5f6-102">VbStrConv.Wide and VbStrConv.Narrow cannot be combined</span></span>

<span data-ttu-id="0b5f6-103">Uygulamanız, `VbStrConv` sabit listesi üyelerini birleştirmeye çalışıyor `Wide` ve `Narrow` birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="0b5f6-103">Your application is trying to combine the `VbStrConv` enumeration members `Wide` and `Narrow`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b5f6-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0b5f6-104">To correct this error</span></span>  
  
1. <span data-ttu-id="0b5f6-105">Ya da ' i kaldırın `VbStrConv.Wide` `VbStrConv.Narrow` .</span><span class="sxs-lookup"><span data-stu-id="0b5f6-105">Remove either `VbStrConv.Wide` or `VbStrConv.Narrow`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5f6-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b5f6-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="0b5f6-107">Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin</span><span class="sxs-lookup"><span data-stu-id="0b5f6-107">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
