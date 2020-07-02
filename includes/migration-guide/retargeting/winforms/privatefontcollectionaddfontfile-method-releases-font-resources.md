---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614899"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a><span data-ttu-id="af7ea-101">PrivateFontCollection. AddFontFile yöntemi, yazı tipi kaynaklarını yayınlar</span><span class="sxs-lookup"><span data-stu-id="af7ea-101">PrivateFontCollection.AddFontFile method releases Font resources</span></span>

#### <a name="details"></a><span data-ttu-id="af7ea-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="af7ea-102">Details</span></span>

<span data-ttu-id="af7ea-103">.NET Framework 4.7.1 ve önceki sürümlerde, <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> sınıfı, <xref:System.Drawing.Text.PrivateFontCollection> <xref:System.Drawing.Font> yöntemi kullanılarak bu koleksiyona eklenen nesneler için ATıLDıKTAN sonra GDI+ yazı tipi kaynaklarını serbest bırakmaz <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> .</span><span class="sxs-lookup"><span data-stu-id="af7ea-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> class does not release the GDI+ font resources after the <xref:System.Drawing.Text.PrivateFontCollection> is disposed for <xref:System.Drawing.Font> objects that are added to this collection using the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> method.</span></span> <span data-ttu-id="af7ea-104">.NET Framework 4.7.2 ve üzeri, <xref:System.Drawing.Text.FontCollection.Dispose%2A> koleksiyona dosya olarak eklenmiş olan GDI+ yazı tiplerini yayınlar.</span><span class="sxs-lookup"><span data-stu-id="af7ea-104">In the .NET Framework 4.7.2 and later <xref:System.Drawing.Text.FontCollection.Dispose%2A> releases the GDI+ fonts that were added to the collection as files.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af7ea-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="af7ea-105">Suggestion</span></span>

<span data-ttu-id="af7ea-106">**Bu değişiklikleri kabul etme veya devre dışı bırakma** Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af7ea-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="af7ea-107">Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="af7ea-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="af7ea-108">.NET Framework 4.7.2 hedeflemek için yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="af7ea-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="af7ea-109">Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="af7ea-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="af7ea-110">Aşağıdaki örnekte gösterildiği gibi, .NET Framework 4.7.1 veya daha önceki bir sürümü hedefler ve eski erişilebilirlik davranışlarından yararlanarak, aşağıdaki [AppContext anahtarını](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` app.config dosyasının bölümüne ekleyerek ve öğesini olarak ayarlayarak eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .</span><span class="sxs-lookup"><span data-stu-id="af7ea-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="af7ea-111">.NET Framework 4.7.2 veya üstünü hedefleyen ve eski davranışı korumak isteyen uygulamalar, bu AppContext anahtarını açıkça ayarlayarak yazı tipi kaynaklarını serbest bırakmaya izin verebilir `true` .</span><span class="sxs-lookup"><span data-stu-id="af7ea-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to not release font resources by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="af7ea-112">Name</span><span class="sxs-lookup"><span data-stu-id="af7ea-112">Name</span></span>    | <span data-ttu-id="af7ea-113">Değer</span><span class="sxs-lookup"><span data-stu-id="af7ea-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af7ea-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="af7ea-114">Scope</span></span>   | <span data-ttu-id="af7ea-115">Edge</span><span class="sxs-lookup"><span data-stu-id="af7ea-115">Edge</span></span>        |
| <span data-ttu-id="af7ea-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="af7ea-116">Version</span></span> | <span data-ttu-id="af7ea-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="af7ea-117">4.7.2</span></span>       |
| <span data-ttu-id="af7ea-118">Tür</span><span class="sxs-lookup"><span data-stu-id="af7ea-118">Type</span></span>    | <span data-ttu-id="af7ea-119">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="af7ea-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="af7ea-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="af7ea-120">Affected APIs</span></span>

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
