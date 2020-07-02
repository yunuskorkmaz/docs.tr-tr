---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620547"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="17eb1-101">IPad artık bir tarayıcı özelliği olduğundan, IPad özel özellikler dosyasında kullanılmamalıdır</span><span class="sxs-lookup"><span data-stu-id="17eb1-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="17eb1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="17eb1-102">Details</span></span>

<span data-ttu-id="17eb1-103">İPad .NET Framework 4,5 ' den başlayarak, varsayılan ASP.NET Browser özellikleri dosyasındaki bir tanıtıcıdır, bu nedenle özel bir yetenekler dosyasında kullanılmamalıdır</span><span class="sxs-lookup"><span data-stu-id="17eb1-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="17eb1-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="17eb1-104">Suggestion</span></span>

<span data-ttu-id="17eb1-105">İPad 'e özgü yetenekler gerekliyse, &quot; &quot; &quot; &quot; Kullanıcı Aracısı eşleştirmesi tarafından yeni bir iPad kimliği oluşturmak yerine önceden tanımlanmış ağ geçidi yeniden oluşturma iPad üzerinde özellikleri ayarlayarak iPad davranışını değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="17eb1-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="17eb1-106">Name</span><span class="sxs-lookup"><span data-stu-id="17eb1-106">Name</span></span>    | <span data-ttu-id="17eb1-107">Değer</span><span class="sxs-lookup"><span data-stu-id="17eb1-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="17eb1-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="17eb1-108">Scope</span></span>   |<span data-ttu-id="17eb1-109">Edge</span><span class="sxs-lookup"><span data-stu-id="17eb1-109">Edge</span></span>|
|<span data-ttu-id="17eb1-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="17eb1-110">Version</span></span>|<span data-ttu-id="17eb1-111">4,5</span><span class="sxs-lookup"><span data-stu-id="17eb1-111">4.5</span></span>|
|<span data-ttu-id="17eb1-112">Tür</span><span class="sxs-lookup"><span data-stu-id="17eb1-112">Type</span></span>|<span data-ttu-id="17eb1-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="17eb1-113">Runtime</span></span>|
