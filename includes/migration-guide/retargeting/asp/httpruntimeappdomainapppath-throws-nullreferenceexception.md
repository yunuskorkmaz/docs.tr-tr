---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859137"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="0ee55-101">httpRuntime.AppDomainAppPath NullReferenceException atar</span><span class="sxs-lookup"><span data-stu-id="0ee55-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0ee55-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0ee55-102">Details</span></span>|<span data-ttu-id="0ee55-103">.NET Framework 4.6.2'de, null karakterleri <code>T:System.NullReferenceException</code> içeren bir <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> değer alırken çalışma zamanı bir değer atar. .NET Framework 4.6.1 ve önceki sürümlerinde, çalışma <code>T:System.ArgumentNullException</code>zamanı .</span><span class="sxs-lookup"><span data-stu-id="0ee55-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="0ee55-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="0ee55-104">Suggestion</span></span>|<span data-ttu-id="0ee55-105">Bu değişikliğe yanıt vermek için aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ee55-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="0ee55-106"><code>T:System.NullReferenceException</code> .NET Framework 4.6.2 üzerinde çalışan uygulama varsa ele alın.</span><span class="sxs-lookup"><span data-stu-id="0ee55-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="0ee55-107">Önceki davranışı geri yükleyen ve bir <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="0ee55-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="0ee55-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0ee55-108">Scope</span></span>|<span data-ttu-id="0ee55-109">Edge</span><span class="sxs-lookup"><span data-stu-id="0ee55-109">Edge</span></span>|
|<span data-ttu-id="0ee55-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0ee55-110">Version</span></span>|<span data-ttu-id="0ee55-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="0ee55-111">4.6.2</span></span>|
|<span data-ttu-id="0ee55-112">Tür</span><span class="sxs-lookup"><span data-stu-id="0ee55-112">Type</span></span>|<span data-ttu-id="0ee55-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="0ee55-113">Retargeting</span></span>|
|<span data-ttu-id="0ee55-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0ee55-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
