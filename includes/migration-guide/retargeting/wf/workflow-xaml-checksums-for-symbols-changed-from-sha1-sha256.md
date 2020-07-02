---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616295"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="7967a-101">Semboller için iş akışı XAML sağlama toplamı, SHA1 'den SHA256 'e değişti</span><span class="sxs-lookup"><span data-stu-id="7967a-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="7967a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7967a-102">Details</span></span>

<span data-ttu-id="7967a-103">Visual Studio ile hata ayıklamayı desteklemek için, Iş akışı çalışma zamanı bir karma algoritması kullanarak bir iş akışı XAML dosyası için bir sağlama toplamı üretir.</span><span class="sxs-lookup"><span data-stu-id="7967a-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="7967a-104">.NET Framework 4.6.2 ve önceki sürümlerde, iş akışı sağlama toplamı karması, FIPS özellikli sistemlerde sorun oluşmasına neden olan MD5 algoritmasını kullandı.</span><span class="sxs-lookup"><span data-stu-id="7967a-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="7967a-105">4,7 .NET Framework başlayarak, varsayılan algoritma SHA1 olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7967a-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="7967a-106">4,8 .NET Framework başlayarak, varsayılan algoritma SHA256 olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7967a-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7967a-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="7967a-107">Suggestion</span></span>

<span data-ttu-id="7967a-108">Kodunuz iş akışı örneklerini yükleyemediğinden veya bir sağlama toplamı hatası nedeniyle uygun sembolleri bulamadı, `AppContext` "Switch.SysTItem anahtarını ayarlamayı deneyin. Activities. UseSHA1HashForDebuggerSymbols " `true` .</span><span class="sxs-lookup"><span data-stu-id="7967a-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="7967a-109">Kod:</span><span class="sxs-lookup"><span data-stu-id="7967a-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="7967a-110">Ya da yapılandırmada:</span><span class="sxs-lookup"><span data-stu-id="7967a-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="7967a-111">Name</span><span class="sxs-lookup"><span data-stu-id="7967a-111">Name</span></span>    | <span data-ttu-id="7967a-112">Değer</span><span class="sxs-lookup"><span data-stu-id="7967a-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7967a-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7967a-113">Scope</span></span>   | <span data-ttu-id="7967a-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="7967a-114">Minor</span></span>       |
| <span data-ttu-id="7967a-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7967a-115">Version</span></span> | <span data-ttu-id="7967a-116">4,8</span><span class="sxs-lookup"><span data-stu-id="7967a-116">4.8</span></span>         |
| <span data-ttu-id="7967a-117">Tür</span><span class="sxs-lookup"><span data-stu-id="7967a-117">Type</span></span>    | <span data-ttu-id="7967a-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="7967a-118">Retargeting</span></span> |
