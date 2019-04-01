---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760351"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="e9e7a-101">Bazı .NET SDK Araçları için geliştirilmiş erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="e9e7a-101">Improved accessibility for some .NET SDK tools</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e9e7a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e9e7a-102">Details</span></span>|<span data-ttu-id="e9e7a-103">.NET Framework SDK içinde 4.7.1 SvcConfigEditor.exe ve SvcTraceViewer.exe Araçlar çeşitli erişilebilirlik sorunları çözme tarafından geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9e7a-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="e9e7a-104">Bunların çoğu tanımlanmayan bir ad veya doğru uygulanmadı belirli bir UI Otomasyon düzenleri gibi küçük problemler yoktu.</span><span class="sxs-lookup"><span data-stu-id="e9e7a-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="e9e7a-105">Çok sayıda kullanıcı yanlış bu değerlerin farkında olmaz mıydı ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9e7a-105">While many users wouldn’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="e9e7a-106">Elbette bu düzeltmeler klavye odağı sırası gibi önceki bazı davranışları değiştirir. Tüm bu araçlarda erişilebilirlik düzeltmeleri almak için app.config dosyanıza aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e7a-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e9e7a-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e9e7a-107">Scope</span></span>|<span data-ttu-id="e9e7a-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="e9e7a-108">Edge</span></span>|
|<span data-ttu-id="e9e7a-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e9e7a-109">Version</span></span>|<span data-ttu-id="e9e7a-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e9e7a-110">4.7.1</span></span>|
|<span data-ttu-id="e9e7a-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e9e7a-111">Type</span></span>|<span data-ttu-id="e9e7a-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e9e7a-112">Retargeting</span></span>|

