---
title: Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: aa97ae420a0a289979fe86db373c635361dc6475
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874640"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="10542-102">Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="10542-102">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="10542-103">Ya da işlev çağrısında belirttiğiniz sınıf, `GetObject` `CreateObject` bir programlama arabirimi açığa çıkarmıyor veya bir projeyi. dll ' den. exe ' ye veya bunun tersini değiştirmiş.</span><span class="sxs-lookup"><span data-stu-id="10542-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10542-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="10542-104">To correct this error</span></span>  
  
1. <span data-ttu-id="10542-105">Bu nesne sınıfıyla Otomasyon kullanımıyla ilgili sınırlamalar için nesneyi oluşturan uygulamanın belgelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10542-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="10542-106">Bir projeyi. dll ' den. exe ' ye veya bunun tersini değiştirdiyseniz, eski. dll veya. exe ' nin kaydını el ile kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="10542-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10542-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10542-107">See also</span></span>

- [<span data-ttu-id="10542-108">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="10542-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="10542-109">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="10542-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
