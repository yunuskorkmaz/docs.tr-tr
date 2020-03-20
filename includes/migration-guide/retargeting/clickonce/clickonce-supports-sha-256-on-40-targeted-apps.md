---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804556"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="0e336-101">ClickOnce, 4.0 hedefli uygulamalarda SHA-256'yı destekler</span><span class="sxs-lookup"><span data-stu-id="0e336-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0e336-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0e336-102">Details</span></span>|<span data-ttu-id="0e336-103">Önceden, SHA-256 ile imzalanmış bir sertifikaya sahip bir ClickOnce uygulaması, uygulama 4.0'ı hedeflese bile .NET Framework 4.5 veya daha sonra sının bulunmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0e336-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="0e336-104">Şimdi, .NET Framework 4.0 hedefli ClickOnce uygulamaları SHA-256 ile imzalanmış olsa bile .NET Framework 4.0 üzerinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e336-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="0e336-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="0e336-105">Suggestion</span></span>|<span data-ttu-id="0e336-106">Bu değişiklik bu bağımlılığı ortadan kaldırır ve SHA-256 sertifikalarının .NET Framework 4 ve önceki sürümleri hedefleyen ClickOnce uygulamalarını imzalamak için kullanılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0e336-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="0e336-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0e336-107">Scope</span></span>|<span data-ttu-id="0e336-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="0e336-108">Minor</span></span>|
|<span data-ttu-id="0e336-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e336-109">Version</span></span>|<span data-ttu-id="0e336-110">4.6</span><span class="sxs-lookup"><span data-stu-id="0e336-110">4.6</span></span>|
|<span data-ttu-id="0e336-111">Tür</span><span class="sxs-lookup"><span data-stu-id="0e336-111">Type</span></span>|<span data-ttu-id="0e336-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="0e336-112">Retargeting</span></span>|
