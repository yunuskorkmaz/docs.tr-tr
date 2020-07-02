---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614912"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="681dd-101">WinForm 'ın etki alanı UpButton ve DownButton eylemleri şimdi eşitlendi</span><span class="sxs-lookup"><span data-stu-id="681dd-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="681dd-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="681dd-102">Details</span></span>

<span data-ttu-id="681dd-103">.NET Framework 4.7.1 ve önceki sürümlerde denetim <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> metni mevcut olduğunda denetim eylemi yok sayılır ve geliştirici, <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylem kullanılmadan önce denetimde eylemi kullanmak için gereklidir <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="681dd-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="681dd-104">.NET Framework başlayarak, hem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> hem de <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemleri bu senaryoda bağımsız olarak çalışır ve eşitlenmiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="681dd-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="681dd-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="681dd-105">Suggestion</span></span>

<span data-ttu-id="681dd-106">Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="681dd-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="681dd-107">Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="681dd-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="681dd-108">.NET Framework 4.7.2 hedeflemek için yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="681dd-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="681dd-109">Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="681dd-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="681dd-110">Aşağıdaki [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` `false` örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve olarak ayarlayarak eski kaydırma davranışının yerine geçer.</span><span class="sxs-lookup"><span data-stu-id="681dd-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="681dd-111">Name</span><span class="sxs-lookup"><span data-stu-id="681dd-111">Name</span></span>    | <span data-ttu-id="681dd-112">Değer</span><span class="sxs-lookup"><span data-stu-id="681dd-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="681dd-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="681dd-113">Scope</span></span>   | <span data-ttu-id="681dd-114">Edge</span><span class="sxs-lookup"><span data-stu-id="681dd-114">Edge</span></span>        |
| <span data-ttu-id="681dd-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="681dd-115">Version</span></span> | <span data-ttu-id="681dd-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="681dd-116">4.7.2</span></span>       |
| <span data-ttu-id="681dd-117">Tür</span><span class="sxs-lookup"><span data-stu-id="681dd-117">Type</span></span>    | <span data-ttu-id="681dd-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="681dd-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="681dd-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="681dd-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
