---
title: "' Period ' bağımsız değişkeni, ' Life ' bağımsız değişkenine eşit veya ondan küçük olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 844192f1168e6fef7906ffc133dcc3b5ba40b42c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087043"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a><span data-ttu-id="6b385-102">' Period ' bağımsız değişkeni, ' Life ' bağımsız değişkenine eşit veya ondan küçük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="6b385-102">Argument 'Period' must be less than or equal to argument 'Life'</span></span>

<span data-ttu-id="6b385-103">`Period`Varlık amortismanının hesaplandığı dönemi belirten bağımsız değişkenin değeri, `Life` bağımsız değişkenin değerinden büyüktür.</span><span class="sxs-lookup"><span data-stu-id="6b385-103">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b385-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6b385-104">To correct this error</span></span>  
  
- <span data-ttu-id="6b385-105">`Life`Ve `Period` bağımsız değişkenlerinin aynı birimlerde belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6b385-105">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="6b385-106">Örneğin, `Life` ay cinsinden ölçüldüğünde `Period` de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b385-106">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b385-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b385-107">See also</span></span>

- [<span data-ttu-id="6b385-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="6b385-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
