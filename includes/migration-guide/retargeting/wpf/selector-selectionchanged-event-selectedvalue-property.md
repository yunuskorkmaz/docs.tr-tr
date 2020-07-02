---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614940"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="27e73-101">Seçici SelectionChanged olayı ve SelectedValue özelliği</span><span class="sxs-lookup"><span data-stu-id="27e73-101">Selector SelectionChanged event and SelectedValue property</span></span>

#### <a name="details"></a><span data-ttu-id="27e73-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="27e73-102">Details</span></span>

<span data-ttu-id="27e73-103">.NET Framework 4.7.1 başlayarak, bir, <xref:System.Windows.Controls.Primitives.Selector> seçimi değiştiğinde olayı oluşturmadan önce her zaman <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliğinin değerini günceller <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> .</span><span class="sxs-lookup"><span data-stu-id="27e73-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="27e73-104">Bu, SelectedValue özelliğini, <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> olayı oluşturmadan önce güncellenen diğer seçim özellikleriyle (ve) tutarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="27e73-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="27e73-105">.NET Framework 4,7 ve önceki sürümlerde, SelectedValue 'nin güncelleştirilmesi çoğu durumda olaydan önce gerçekleşti, ancak seçim değişikliği özelliği değiştirilmediğinde olay sonrasında gerçekleşiyor <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="27e73-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="27e73-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="27e73-106">Suggestion</span></span>

<span data-ttu-id="27e73-107">.NET Framework 4.7.1 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski davranışı kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="27e73-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="27e73-108">.NET Framework 4,7 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışan uygulamalar, `<runtime>` uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yeni davranışı etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="27e73-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="27e73-109">Name</span><span class="sxs-lookup"><span data-stu-id="27e73-109">Name</span></span>    | <span data-ttu-id="27e73-110">Değer</span><span class="sxs-lookup"><span data-stu-id="27e73-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27e73-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="27e73-111">Scope</span></span>   | <span data-ttu-id="27e73-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="27e73-112">Minor</span></span>       |
| <span data-ttu-id="27e73-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="27e73-113">Version</span></span> | <span data-ttu-id="27e73-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="27e73-114">4.7.1</span></span>       |
| <span data-ttu-id="27e73-115">Tür</span><span class="sxs-lookup"><span data-stu-id="27e73-115">Type</span></span>    | <span data-ttu-id="27e73-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="27e73-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="27e73-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="27e73-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
