---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614842"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="43337-101">İş akışı sağlama toplamı, MD5 'den SHA1 'ye değişti</span><span class="sxs-lookup"><span data-stu-id="43337-101">Workflow checksums changed from MD5 to SHA1</span></span>

#### <a name="details"></a><span data-ttu-id="43337-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="43337-102">Details</span></span>

<span data-ttu-id="43337-103">Visual Studio ile hata ayıklamayı desteklemek için, Iş akışı çalışma zamanı bir karma algoritması kullanarak bir iş akışı örneği için bir sağlama toplamı üretir.</span><span class="sxs-lookup"><span data-stu-id="43337-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="43337-104">.NET Framework 4.6.2 ve önceki sürümlerde, iş akışı sağlama toplamı karması, FIPS özellikli sistemlerde sorun oluşmasına neden olan MD5 algoritmasını kullandı.</span><span class="sxs-lookup"><span data-stu-id="43337-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="43337-105">4,7 .NET Framework başlayarak algoritma SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="43337-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="43337-106">Kodunuz bu sağlama toplamlarını kalıcı hale alıyorsa, bunlar uyumsuz olur.</span><span class="sxs-lookup"><span data-stu-id="43337-106">If your code has persisted these checksums, they will be incompatible.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="43337-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="43337-107">Suggestion</span></span>

<span data-ttu-id="43337-108">Kodunuz, sağlama toplamı hatası nedeniyle iş akışı örneklerini yükleyememesi durumunda, `AppContext` anahtarı &quot;Switch.Sysdıtem ayarlamayı deneyin. Activities. UseMD5ForWFDebugger &quot; . Kodda:</span><span class="sxs-lookup"><span data-stu-id="43337-108">If your code is unable to load workflow instances due to a checksum failure, try setting the `AppContext` switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

<span data-ttu-id="43337-109">Ya da yapılandırmada:</span><span class="sxs-lookup"><span data-stu-id="43337-109">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="43337-110">Name</span><span class="sxs-lookup"><span data-stu-id="43337-110">Name</span></span>    | <span data-ttu-id="43337-111">Değer</span><span class="sxs-lookup"><span data-stu-id="43337-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="43337-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="43337-112">Scope</span></span>   | <span data-ttu-id="43337-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="43337-113">Minor</span></span>       |
| <span data-ttu-id="43337-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="43337-114">Version</span></span> | <span data-ttu-id="43337-115">4,7</span><span class="sxs-lookup"><span data-stu-id="43337-115">4.7</span></span>         |
| <span data-ttu-id="43337-116">Tür</span><span class="sxs-lookup"><span data-stu-id="43337-116">Type</span></span>    | <span data-ttu-id="43337-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="43337-117">Retargeting</span></span> |
