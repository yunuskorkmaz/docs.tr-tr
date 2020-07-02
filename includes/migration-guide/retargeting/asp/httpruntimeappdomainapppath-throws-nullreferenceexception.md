---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617553"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="5763e-101">HttpRuntime. AppDomainAppPath bir NullReferenceException oluşturur</span><span class="sxs-lookup"><span data-stu-id="5763e-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="5763e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5763e-102">Details</span></span>

<span data-ttu-id="5763e-103">.NET Framework 4.6.2, çalışma zamanı null karakterler içeren bir `T:System.NullReferenceException` değer alınırken bir oluşturur `P:System.Web.HttpRuntime.AppDomainAppPath` . .NET Framework 4.6.1 ve önceki sürümlerde, çalışma zamanı bir oluşturur `T:System.ArgumentNullException` .</span><span class="sxs-lookup"><span data-stu-id="5763e-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5763e-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="5763e-104">Suggestion</span></span>

<span data-ttu-id="5763e-105">Bu değişikliğe yanıt vermek için şu iki seçenekten birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5763e-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="5763e-106">`T:System.NullReferenceException`Uygulama .NET Framework 4.6.2 üzerinde çalışıyorsa işleyin.</span><span class="sxs-lookup"><span data-stu-id="5763e-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="5763e-107">Önceki davranışı geri yükleyen ve bir oluşturan .NET Framework 4,7 ' a yükseltin `T:System.ArgumentNullException` .</span><span class="sxs-lookup"><span data-stu-id="5763e-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="5763e-108">Name</span><span class="sxs-lookup"><span data-stu-id="5763e-108">Name</span></span>    | <span data-ttu-id="5763e-109">Değer</span><span class="sxs-lookup"><span data-stu-id="5763e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5763e-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5763e-110">Scope</span></span>   | <span data-ttu-id="5763e-111">Edge</span><span class="sxs-lookup"><span data-stu-id="5763e-111">Edge</span></span>        |
| <span data-ttu-id="5763e-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5763e-112">Version</span></span> | <span data-ttu-id="5763e-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="5763e-113">4.6.2</span></span>       |
| <span data-ttu-id="5763e-114">Tür</span><span class="sxs-lookup"><span data-stu-id="5763e-114">Type</span></span>    | <span data-ttu-id="5763e-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="5763e-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5763e-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5763e-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
