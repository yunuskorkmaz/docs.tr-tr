---
title: SimplifiedChinese ve VbStrConv. TraditionalChinese birleştirilemez
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_StrConvSCandTC
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
ms.openlocfilehash: 512651add89de23b35512e736dbf74f0891c995a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91060490"
---
# <a name="simplifiedchinese-and-vbstrconvtraditionalchinese-cannot-be-combined"></a><span data-ttu-id="80278-102">SimplifiedChinese ve VbStrConv. TraditionalChinese birleştirilemez</span><span class="sxs-lookup"><span data-stu-id="80278-102">SimplifiedChinese and VbStrConv.TraditionalChinese cannot be combined</span></span>

<span data-ttu-id="80278-103">Uygulamanız, `VbStrConv` sabit listesi üyelerini birleştirmeye çalışıyor `SimplifiedChinese` ve `TraditionalChinese` birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="80278-103">Your application is attempting to combine the `VbStrConv` enumeration members `SimplifiedChinese` and `TraditionalChinese`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80278-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="80278-104">To correct this error</span></span>  
  
- <span data-ttu-id="80278-105">Ya da ' i kaldırın `VbStrConv.SimplifiedChinese` `VbStrConv.TraditionalChinese` .</span><span class="sxs-lookup"><span data-stu-id="80278-105">Remove either `VbStrConv.SimplifiedChinese` or `VbStrConv.TraditionalChinese`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80278-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80278-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="80278-107">Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin</span><span class="sxs-lookup"><span data-stu-id="80278-107">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
