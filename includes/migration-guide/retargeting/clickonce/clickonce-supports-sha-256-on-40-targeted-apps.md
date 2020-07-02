---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615745"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="f8a23-101">ClickOnce, 4,0 hedefli uygulamalarda SHA-256 ' i destekler</span><span class="sxs-lookup"><span data-stu-id="f8a23-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="f8a23-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f8a23-102">Details</span></span>

<span data-ttu-id="f8a23-103">Daha önce, SHA-256 ile imzalanmış bir sertifika olan bir ClickOnce uygulaması, uygulama ' i 4,0 hedeflese bile .NET Framework 4,5 veya üzeri bir sürümü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8a23-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="f8a23-104">Şimdi, .NET Framework 4,0-hedeflenen ClickOnce uygulamaları SHA-256 ile imzalanmış olsa bile .NET Framework 4,0 üzerinde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="f8a23-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f8a23-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="f8a23-105">Suggestion</span></span>

<span data-ttu-id="f8a23-106">Bu değişiklik, bu bağımlılığı ortadan kaldırır ve .NET Framework 4 ve önceki sürümleri hedefleyen ClickOnce uygulamalarını imzalamak için SHA-256 sertifikalarının kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f8a23-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="f8a23-107">Name</span><span class="sxs-lookup"><span data-stu-id="f8a23-107">Name</span></span>    | <span data-ttu-id="f8a23-108">Değer</span><span class="sxs-lookup"><span data-stu-id="f8a23-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f8a23-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f8a23-109">Scope</span></span>   | <span data-ttu-id="f8a23-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="f8a23-110">Minor</span></span>       |
| <span data-ttu-id="f8a23-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f8a23-111">Version</span></span> | <span data-ttu-id="f8a23-112">4.6</span><span class="sxs-lookup"><span data-stu-id="f8a23-112">4.6</span></span>         |
| <span data-ttu-id="f8a23-113">Tür</span><span class="sxs-lookup"><span data-stu-id="f8a23-113">Type</span></span>    | <span data-ttu-id="f8a23-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="f8a23-114">Retargeting</span></span> |
