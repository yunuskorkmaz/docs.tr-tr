---
title: Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 856c3f5ef503a7e5919e9e602532c56d9557482f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415407"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="931fa-102">Sınıf Otomasyonu veya beklenen arabirimi desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="931fa-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="931fa-103">Ya da işlev çağrısında belirttiğiniz sınıf, `GetObject` `CreateObject` bir programlama arabirimi açığa çıkarmıyor veya bir projeyi. dll ' den. exe ' ye veya bunun tersini değiştirmiş.</span><span class="sxs-lookup"><span data-stu-id="931fa-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="931fa-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="931fa-104">To correct this error</span></span>  
  
1. <span data-ttu-id="931fa-105">Bu nesne sınıfıyla Otomasyon kullanımıyla ilgili sınırlamalar için nesneyi oluşturan uygulamanın belgelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="931fa-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="931fa-106">Bir projeyi. dll ' den. exe ' ye veya bunun tersini değiştirdiyseniz, eski. dll veya. exe ' nin kaydını el ile kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="931fa-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931fa-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="931fa-107">See also</span></span>

- [<span data-ttu-id="931fa-108">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="931fa-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="931fa-109">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="931fa-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
