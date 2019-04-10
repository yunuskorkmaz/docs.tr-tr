---
title: Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 4545c6d3bc302dba0c37e5ae6ebefa8939b0cff9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305929"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="6ad61-102">Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="6ad61-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="6ad61-103">İçinde belirtilen sınıf `GetObject` veya `CreateObject` işlev çağrısı bir programlama arabirimi ifşa veya bir proje için .exe, .dll dosyasından değiştirilmiş ya da tam tersi.</span><span class="sxs-lookup"><span data-stu-id="6ad61-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ad61-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6ad61-104">To correct this error</span></span>  
  
1. <span data-ttu-id="6ad61-105">Bu nesnenin sınıfını otomasyonla kullanımı ile ilgili sınırlamalar için nesneyi oluşturan uygulamanın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6ad61-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="6ad61-106">Bir proje için .exe veya .dll dosyasından değiştirdiyseniz, eski .dll veya .exe el ile kaydı gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ad61-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad61-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ad61-107">See also</span></span>

- [<span data-ttu-id="6ad61-108">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="6ad61-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="6ad61-109">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="6ad61-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
