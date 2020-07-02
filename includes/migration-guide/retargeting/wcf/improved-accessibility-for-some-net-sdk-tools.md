---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614829"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="7d795-101">Bazı .NET SDK araçları için iyileştirilmiş erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="7d795-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="7d795-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7d795-102">Details</span></span>

<span data-ttu-id="7d795-103">.NET Framework SDK 4.7.1, SvcConfigEditor.exe ve SvcTraceViewer.exe araçları, değişen erişilebilirlik sorunlarını düzelterek geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7d795-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="7d795-104">Bunların çoğu, bir ad tanımlanmamış veya belirli UI Otomasyon desenlerinin doğru uygulanmadığını küçük sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="7d795-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="7d795-105">Birçok kullanıcı bu hatalı değerleri farkında olmasa da ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK araçlarını daha erişilebilir bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="7d795-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="7d795-106">Kesinlikle, bu düzeltmeler klavye odağı sırası gibi önceki bazı davranışları değiştirir. Bu araçlarınızdaki tüm erişilebilirlik düzeltmelerini almak için app.config dosyanıza aşağıdaki adımları uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d795-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="7d795-107">Name</span><span class="sxs-lookup"><span data-stu-id="7d795-107">Name</span></span>    | <span data-ttu-id="7d795-108">Değer</span><span class="sxs-lookup"><span data-stu-id="7d795-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7d795-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7d795-109">Scope</span></span>   | <span data-ttu-id="7d795-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7d795-110">Edge</span></span>        |
| <span data-ttu-id="7d795-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7d795-111">Version</span></span> | <span data-ttu-id="7d795-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="7d795-112">4.7.1</span></span>       |
| <span data-ttu-id="7d795-113">Tür</span><span class="sxs-lookup"><span data-stu-id="7d795-113">Type</span></span>    | <span data-ttu-id="7d795-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="7d795-114">Retargeting</span></span> |
