---
ms.openlocfilehash: c64431fd651fd7d53fb46231c6acc10c5cb43fff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606304"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="8818d-101">WinForm 'ın etki alanı UpButton ve DownButton eylemleri şimdi eşitlendi</span><span class="sxs-lookup"><span data-stu-id="8818d-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="8818d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8818d-102">Details</span></span>

<span data-ttu-id="8818d-103">.NET Framework 4.7.1 ve önceki sürümlerde denetim <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> metni mevcut olduğunda denetim eylemi yok sayılır ve geliştirici, <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylem kullanılmadan önce denetimde eylemi kullanmak için gereklidir <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8818d-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="8818d-104">.NET Framework başlayarak, hem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> hem de <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemleri bu senaryoda bağımsız olarak çalışır ve eşitlenmiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="8818d-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8818d-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8818d-105">Suggestion</span></span>

<span data-ttu-id="8818d-106">Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8818d-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="8818d-107">Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="8818d-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="8818d-108">.NET Framework 4.7.2 hedeflemek için yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="8818d-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="8818d-109">Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8818d-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="8818d-110">Aşağıdaki [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` `false` örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve olarak ayarlayarak eski kaydırma davranışının yerine geçer.</span><span class="sxs-lookup"><span data-stu-id="8818d-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8818d-111">Name</span><span class="sxs-lookup"><span data-stu-id="8818d-111">Name</span></span>    | <span data-ttu-id="8818d-112">Değer</span><span class="sxs-lookup"><span data-stu-id="8818d-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8818d-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8818d-113">Scope</span></span>   | <span data-ttu-id="8818d-114">Edge</span><span class="sxs-lookup"><span data-stu-id="8818d-114">Edge</span></span>        |
| <span data-ttu-id="8818d-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8818d-115">Version</span></span> | <span data-ttu-id="8818d-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8818d-116">4.7.2</span></span>       |
| <span data-ttu-id="8818d-117">Tür</span><span class="sxs-lookup"><span data-stu-id="8818d-117">Type</span></span>    | <span data-ttu-id="8818d-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="8818d-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8818d-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8818d-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
