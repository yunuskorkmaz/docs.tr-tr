---
ms.openlocfilehash: d4f22aa41eb7aeffd655d980cb8418649462273e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757790"
---
## <a name="introduction"></a><span data-ttu-id="6c37f-101">Giriş</span><span class="sxs-lookup"><span data-stu-id="6c37f-101">Introduction</span></span>
<span data-ttu-id="6c37f-102">Yeniden hedefleme değişiklikleri farklı bir .NET Framework'ü hedefleyen için derlenen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6c37f-102">Retargeting changes affect apps that are recompiled to target a different .NET Framework.</span></span> <span data-ttu-id="6c37f-103">Bunlara aşağıdakiler dahildir:</span><span class="sxs-lookup"><span data-stu-id="6c37f-103">They include:</span></span>

* <span data-ttu-id="6c37f-104">Tasarım zamanı ortamındaki değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="6c37f-104">Changes in the design-time environment.</span></span> <span data-ttu-id="6c37f-105">Örneğin, yapı araçları daha önce uyarı göstermiyorken şimdi gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6c37f-105">For example, build tools may emit warnings when previously they did not.</span></span>

* <span data-ttu-id="6c37f-106">Çalışma zamanı ortamındaki değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="6c37f-106">Changes in the runtime environment.</span></span> <span data-ttu-id="6c37f-107">Bu, özellikle yeniden hedeflenen .NET Framework'ü hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6c37f-107">These affect only apps that specifically target the retargeted .NET Framework.</span></span> <span data-ttu-id="6c37f-108">.NET Framework'ün önceki sürümlerini hedefleyen uygulamalar, o sürümler altında çalıştıkları gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="6c37f-108">Apps that target previous versions of the .NET Framework behave as they did when running under those versions.</span></span>

<span data-ttu-id="6c37f-109">Yeniden hedefleme değişikliklerinin açıklandığı konularda, biz tek tek öğeleri beklenen etkilerine göre şu şekilde sınıflandırılan:</span><span class="sxs-lookup"><span data-stu-id="6c37f-109">In the topics that describe retargeting changes, we have classified individual items by their expected impact, as follows:</span></span>

<span data-ttu-id="6c37f-110">**Ana** , çok sayıda uygulamayı etkileyen veya kod değişikliği gerektiren önemli bir değişiklik budur.</span><span class="sxs-lookup"><span data-stu-id="6c37f-110">**Major** This is a significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="6c37f-111">**Küçük** Bu, az sayıda uygulamayı etkileyen veya az miktarda kod değişikliği gerektiren bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="6c37f-111">**Minor** This is a change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="6c37f-112">**Kenar çalışması** bu uygulamaları yaygın olmayan çok özel senaryolarda etkileyen bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="6c37f-112">**Edge case** This is a change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="6c37f-113">**Saydam** bu uygulamanın geliştiricisi veya kullanıcısı üzerinde fark edilebilir etkisi olan bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="6c37f-113">**Transparent** This is a change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="6c37f-114">Bu değişiklik nedeniyle uygulamada bir düzenleme yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6c37f-114">The app should not require modification because of this change.</span></span>
