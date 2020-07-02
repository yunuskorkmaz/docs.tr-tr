---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614954"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="ca038-101">TabControl SelectionChanged olayı ve SelectedContent özelliği</span><span class="sxs-lookup"><span data-stu-id="ca038-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="ca038-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ca038-102">Details</span></span>

<span data-ttu-id="ca038-103">.NET Framework 4.7.1 ile başlayarak, bir, <xref:System.Windows.Controls.TabControl> <xref:System.Windows.Controls.TabControl.SelectedContent> seçimi değiştiğinde olayı oluşturmadan önce özelliğinin değerini günceller <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . .NET Framework 4,7 ve önceki sürümlerde, SelectedContent güncelleştirmesi olaydan sonra gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="ca038-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca038-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="ca038-104">Suggestion</span></span>

<span data-ttu-id="ca038-105">.NET Framework 4.7.1 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski davranışı kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="ca038-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="ca038-106">.NET Framework 4,7 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışan uygulamalar, `<runtime>` uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yeni davranışı etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="ca038-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ca038-107">Name</span><span class="sxs-lookup"><span data-stu-id="ca038-107">Name</span></span>    | <span data-ttu-id="ca038-108">Değer</span><span class="sxs-lookup"><span data-stu-id="ca038-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca038-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ca038-109">Scope</span></span>   | <span data-ttu-id="ca038-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="ca038-110">Minor</span></span>       |
| <span data-ttu-id="ca038-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ca038-111">Version</span></span> | <span data-ttu-id="ca038-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ca038-112">4.7.1</span></span>       |
| <span data-ttu-id="ca038-113">Tür</span><span class="sxs-lookup"><span data-stu-id="ca038-113">Type</span></span>    | <span data-ttu-id="ca038-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="ca038-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ca038-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ca038-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
