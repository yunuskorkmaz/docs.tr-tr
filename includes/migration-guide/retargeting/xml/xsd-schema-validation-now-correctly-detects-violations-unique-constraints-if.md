---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615776"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="32e42-101">Birleşik anahtarlar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması artık benzersiz kısıtlamaların ihlallerini doğru şekilde algılar</span><span class="sxs-lookup"><span data-stu-id="32e42-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="32e42-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="32e42-102">Details</span></span>

<span data-ttu-id="32e42-103">4,6 ' dan önceki .NET Framework sürümleri, anahtarlardan biri boş olduğunda, XSD doğrulamasına neden olan bileşik anahtarlar üzerinde benzersiz kısıtlamalar algılamaması nedeniyle oluşan bir hataya sahipti.</span><span class="sxs-lookup"><span data-stu-id="32e42-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="32e42-104">4,6 .NET Framework bu sorun düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="32e42-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="32e42-105">Bu, daha doğru doğrulamaya neden olur, ancak daha önce sahip olacağı bazı XML doğrulamaları da neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="32e42-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="32e42-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="32e42-106">Suggestion</span></span>

<span data-ttu-id="32e42-107">Gevllanıcı .NET Framework 4,0 doğrulaması gerekliyse, doğrulama uygulaması .NET Framework sürüm 4,5 ' i (veya önceki bir sürümü) hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="32e42-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="32e42-108">Ancak 4,6 .NET Framework için yeniden hedeflendiğinde, yinelenen bileşik anahtarların (Bu sorunun açıklamasında açıklandığı gibi) doğrulanması beklenmediğinden emin olmak için kod incelemesi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32e42-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="32e42-109">Name</span><span class="sxs-lookup"><span data-stu-id="32e42-109">Name</span></span>    | <span data-ttu-id="32e42-110">Değer</span><span class="sxs-lookup"><span data-stu-id="32e42-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="32e42-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="32e42-111">Scope</span></span>   | <span data-ttu-id="32e42-112">Edge</span><span class="sxs-lookup"><span data-stu-id="32e42-112">Edge</span></span>        |
| <span data-ttu-id="32e42-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="32e42-113">Version</span></span> | <span data-ttu-id="32e42-114">4.6</span><span class="sxs-lookup"><span data-stu-id="32e42-114">4.6</span></span>         |
| <span data-ttu-id="32e42-115">Tür</span><span class="sxs-lookup"><span data-stu-id="32e42-115">Type</span></span>    | <span data-ttu-id="32e42-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="32e42-116">Retargeting</span></span> |
