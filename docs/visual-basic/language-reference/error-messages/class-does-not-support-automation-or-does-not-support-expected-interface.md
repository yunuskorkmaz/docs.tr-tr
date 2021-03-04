---
description: 'Hakkında daha fazla bilgi edinin: sınıfı Otomasyonu desteklemiyor veya beklenen arabirimi desteklemiyor'
title: Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: c173eeddf3a34d6af169b91066199ce7d03cf4ba
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106637"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="5c011-103">Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="5c011-103">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="5c011-104">Ya da işlev çağrısında belirttiğiniz sınıf, `GetObject` `CreateObject` bir programlama arabirimi açığa çıkarmıyor veya bir projeyi. dll ' den. exe ' ye veya bunun tersini değiştirmiş.</span><span class="sxs-lookup"><span data-stu-id="5c011-104">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c011-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5c011-105">To correct this error</span></span>  
  
1. <span data-ttu-id="5c011-106">Bu nesne sınıfıyla Otomasyon kullanımıyla ilgili sınırlamalar için nesneyi oluşturan uygulamanın belgelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5c011-106">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="5c011-107">Bir projeyi. dll ' den. exe ' ye veya bunun tersini değiştirdiyseniz, eski. dll veya. exe ' nin kaydını el ile kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c011-107">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c011-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c011-108">See also</span></span>

- [<span data-ttu-id="5c011-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="5c011-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="5c011-110">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5c011-110">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
