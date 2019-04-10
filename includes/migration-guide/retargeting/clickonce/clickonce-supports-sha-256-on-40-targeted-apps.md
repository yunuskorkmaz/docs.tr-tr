---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234567"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="1be7d-101">ClickOnce uygulamaları 4.0 hedeflenen SHA-256'yı destekler</span><span class="sxs-lookup"><span data-stu-id="1be7d-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1be7d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1be7d-102">Details</span></span>|<span data-ttu-id="1be7d-103">Daha önce SHA-256 ile imzalanmış bir sertifika ile bir ClickOnce uygulamasını bile uygulamanın hedeflenen 4.0 bulunması, .NET Framework 4.5 veya üzeri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1be7d-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="1be7d-104">Şimdi, .NET Framework 4.0 hedefleyen ClickOnce uygulamaları üzerinde .NET Framework 4.0, SHA-256'yı açtıysanız bile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1be7d-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="1be7d-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="1be7d-105">Suggestion</span></span>|<span data-ttu-id="1be7d-106">Bu değişiklik bu bağımlılığı kaldırır ve .NET Framework 4 ve önceki sürümleri hedefleyen ClickOnce uygulamaları imzalamak için SHA-256'yı sertifikaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="1be7d-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="1be7d-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1be7d-107">Scope</span></span>|<span data-ttu-id="1be7d-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="1be7d-108">Minor</span></span>|
|<span data-ttu-id="1be7d-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1be7d-109">Version</span></span>|<span data-ttu-id="1be7d-110">4.6</span><span class="sxs-lookup"><span data-stu-id="1be7d-110">4.6</span></span>|
|<span data-ttu-id="1be7d-111">Tür</span><span class="sxs-lookup"><span data-stu-id="1be7d-111">Type</span></span>|<span data-ttu-id="1be7d-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="1be7d-112">Retargeting</span></span>|
