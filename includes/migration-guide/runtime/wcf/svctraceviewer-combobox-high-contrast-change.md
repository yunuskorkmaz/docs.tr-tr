---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622092"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="4aa0a-101">svcTraceViewer ComboBox yüksek karşıtlık değişikliği</span><span class="sxs-lookup"><span data-stu-id="4aa0a-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="4aa0a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4aa0a-102">Details</span></span>

<span data-ttu-id="4aa0a-103">[Microsoft hizmet Izleme Görüntüleyicisi aracında](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox denetimleri bazı yüksek karşıtlıklı temalarda doğru renkte görüntülenmedi.</span><span class="sxs-lookup"><span data-stu-id="4aa0a-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="4aa0a-104">Sorun .NET Framework 4.7.2 içinde düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="4aa0a-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="4aa0a-105">Ancak, .NET Framework SDK geri uyumluluk gereksinimleri nedeniyle, bu düzeltmeler müşterilere varsayılan olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="4aa0a-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="4aa0a-106">.NET 4,8, svcTraceViewer.exe.config dosyasına aşağıdaki [AppContext yapılandırma anahtarlarını](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu değişikliği yüzeylerine ekler:</span><span class="sxs-lookup"><span data-stu-id="4aa0a-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a><span data-ttu-id="4aa0a-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="4aa0a-107">Suggestion</span></span>

<ul><li><span data-ttu-id="4aa0a-108">Değişiklik, yüksek karşıtlık davranış değişikliğini yapmak istemiyorsanız, svcTraceViewer.exe.config dosyasından aşağıdaki bölümü kaldırarak devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4aa0a-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="4aa0a-109">Name</span><span class="sxs-lookup"><span data-stu-id="4aa0a-109">Name</span></span>    | <span data-ttu-id="4aa0a-110">Değer</span><span class="sxs-lookup"><span data-stu-id="4aa0a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4aa0a-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4aa0a-111">Scope</span></span>   |<span data-ttu-id="4aa0a-112">Edge</span><span class="sxs-lookup"><span data-stu-id="4aa0a-112">Edge</span></span>|
|<span data-ttu-id="4aa0a-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4aa0a-113">Version</span></span>|<span data-ttu-id="4aa0a-114">4,8</span><span class="sxs-lookup"><span data-stu-id="4aa0a-114">4.8</span></span>|
|<span data-ttu-id="4aa0a-115">Tür</span><span class="sxs-lookup"><span data-stu-id="4aa0a-115">Type</span></span>|<span data-ttu-id="4aa0a-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4aa0a-116">Runtime</span></span>|
