---
ms.openlocfilehash: c0a281b05f453b68495e6fa6fca45f3f36a204a3
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804500"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="3465a-101">XSD şema doğrulaması artık doğru şekilde bileşik anahtarlar kullanılır ve bir anahtar boş ise benzersiz kısıtlamalar ihlalleri algılar</span><span class="sxs-lookup"><span data-stu-id="3465a-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3465a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3465a-102">Details</span></span>|<span data-ttu-id="3465a-103">.NET Framework 4.6 önce sürümleri anahtarlarından birini boşsa bileşik anahtarlar benzersiz kısıtlamalar algılamamak üzere XSD doğrulaması nedeniyle bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3465a-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="3465a-104">.NET Framework 4.6, bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3465a-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="3465a-105">Bu, daha doğru doğrulama neden olur, ancak bazı XML içinde değil, daha önce sahip doğrulanıyor sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3465a-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>|
|<span data-ttu-id="3465a-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="3465a-106">Suggestion</span></span>|<span data-ttu-id="3465a-107">Bazı .NET Framework 4.0 doğrulama gerekli değilse, doğrulama uygulamanın sürüm 4.5 (veya öncesi) hedefleyebilirsiniz .NET Framework'ün.</span><span class="sxs-lookup"><span data-stu-id="3465a-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="3465a-108">Ancak, .NET Framework 4. 6'için ' yeniden hedefleme, kod incelemesi yinelenen bileşik anahtarlar (Bu sorunun açıklamasında tanımlandığı gibi) doğrulamak için beklenmiyor emin emin olmak için yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3465a-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>|
|<span data-ttu-id="3465a-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3465a-109">Scope</span></span>|<span data-ttu-id="3465a-110">Kenar</span><span class="sxs-lookup"><span data-stu-id="3465a-110">Edge</span></span>|
|<span data-ttu-id="3465a-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3465a-111">Version</span></span>|<span data-ttu-id="3465a-112">4.6</span><span class="sxs-lookup"><span data-stu-id="3465a-112">4.6</span></span>|
|<span data-ttu-id="3465a-113">Tür</span><span class="sxs-lookup"><span data-stu-id="3465a-113">Type</span></span>|<span data-ttu-id="3465a-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="3465a-114">Retargeting</span></span>|

