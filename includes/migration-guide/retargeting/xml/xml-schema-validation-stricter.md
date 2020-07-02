---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617296"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="b36b3-101">XML şema doğrulaması daha katı</span><span class="sxs-lookup"><span data-stu-id="b36b3-101">XML schema validation is stricter</span></span>

#### <a name="details"></a><span data-ttu-id="b36b3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b36b3-102">Details</span></span>

<span data-ttu-id="b36b3-103">.NET Framework 4.5’te XML şema doğrulaması daha katıdır.</span><span class="sxs-lookup"><span data-stu-id="b36b3-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="b36b3-104">mailto protokolü gibi bir URI öğesini doğrulamak için xsd:anyURI kullanıyorsanız, URI öğesinde boşluklar olduğundan doğrulama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b36b3-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="b36b3-105">.NET Framework'ün önceki sürümlerinde doğrulama başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b36b3-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="b36b3-106">Değişiklik yalnızca .NET Framework 4.5’i hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="b36b3-106">The change affects only applications that target the .NET Framework 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b36b3-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="b36b3-107">Suggestion</span></span>

<span data-ttu-id="b36b3-108">Daha esnek .NET Framework 4.0 doğrulaması gerekiyorsa, doğrulanan uygulama .NET Framework 4.0 sürümünü hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b36b3-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="b36b3-109">Ancak .NET Framework 4.5 yeniden hedeflenirken, geçersiz URI’lerin (boşluk içeren) anyURI veri türüne sahip öznitelik değerleri olarak beklenmediğinden emin olmak için kod incelemesi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b36b3-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>

| <span data-ttu-id="b36b3-110">Name</span><span class="sxs-lookup"><span data-stu-id="b36b3-110">Name</span></span>    | <span data-ttu-id="b36b3-111">Değer</span><span class="sxs-lookup"><span data-stu-id="b36b3-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b36b3-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b36b3-112">Scope</span></span>   | <span data-ttu-id="b36b3-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="b36b3-113">Minor</span></span>       |
| <span data-ttu-id="b36b3-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b36b3-114">Version</span></span> | <span data-ttu-id="b36b3-115">4,5</span><span class="sxs-lookup"><span data-stu-id="b36b3-115">4.5</span></span>         |
| <span data-ttu-id="b36b3-116">Tür</span><span class="sxs-lookup"><span data-stu-id="b36b3-116">Type</span></span>    | <span data-ttu-id="b36b3-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="b36b3-117">Retargeting</span></span> |
