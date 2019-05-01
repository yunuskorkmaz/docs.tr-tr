---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640139"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="9675a-101">XML şema doğrulaması daha katı</span><span class="sxs-lookup"><span data-stu-id="9675a-101">XML schema validation is stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9675a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9675a-102">Details</span></span>|<span data-ttu-id="9675a-103">.NET Framework 4.5’te XML şema doğrulaması daha katıdır.</span><span class="sxs-lookup"><span data-stu-id="9675a-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="9675a-104">mailto protokolü gibi bir URI öğesini doğrulamak için xsd:anyURI kullanıyorsanız, URI öğesinde boşluklar olduğundan doğrulama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9675a-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="9675a-105">.NET Framework'ün önceki sürümlerinde doğrulama başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="9675a-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="9675a-106">Değişiklik yalnızca .NET Framework 4.5’i hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="9675a-106">The change affects only applications that target the .NET Framework 4.5.</span></span>|
|<span data-ttu-id="9675a-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="9675a-107">Suggestion</span></span>|<span data-ttu-id="9675a-108">Daha esnek .NET Framework 4.0 doğrulaması gerekiyorsa, doğrulanan uygulama .NET Framework 4.0 sürümünü hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9675a-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="9675a-109">Ancak .NET Framework 4.5 yeniden hedeflenirken, geçersiz URI’lerin (boşluk içeren) anyURI veri türüne sahip öznitelik değerleri olarak beklenmediğinden emin olmak için kod incelemesi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9675a-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>|
|<span data-ttu-id="9675a-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9675a-110">Scope</span></span>|<span data-ttu-id="9675a-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="9675a-111">Minor</span></span>|
|<span data-ttu-id="9675a-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9675a-112">Version</span></span>|<span data-ttu-id="9675a-113">4,5</span><span class="sxs-lookup"><span data-stu-id="9675a-113">4.5</span></span>|
|<span data-ttu-id="9675a-114">Tür</span><span class="sxs-lookup"><span data-stu-id="9675a-114">Type</span></span>|<span data-ttu-id="9675a-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="9675a-115">Retargeting</span></span>|
