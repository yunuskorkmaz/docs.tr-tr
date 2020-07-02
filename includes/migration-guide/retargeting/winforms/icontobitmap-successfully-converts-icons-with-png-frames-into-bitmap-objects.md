---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615770"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="6d5e5-101">Icon. ToBitmap, PNG çerçevelerinden simgeleri bit eşlem nesnelerine başarıyla dönüştürür</span><span class="sxs-lookup"><span data-stu-id="6d5e5-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

#### <a name="details"></a><span data-ttu-id="6d5e5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6d5e5-102">Details</span></span>

<span data-ttu-id="6d5e5-103">.NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> YÖNTEMI png çerçevelerinden simgeleri bit eşlem nesnelerine başarıyla dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6d5e5-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="6d5e5-104">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> SIMGE nesnesi png çerçevelerdeyse Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d5e5-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="6d5e5-105">Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve <xref:System.ArgumentOutOfRangeException> bir simge NESNESI png çerçevesine sahip olduğunda oluşturulan için özel işleme uygulayan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6d5e5-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="6d5e5-106">.NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="6d5e5-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6d5e5-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="6d5e5-107">Suggestion</span></span>

<span data-ttu-id="6d5e5-108">Bu davranış istenmez ise, app.config dosyanızın bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="6d5e5-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the `<runtime>` section of your app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

<span data-ttu-id="6d5e5-109">app.config dosyası öğesi zaten içeriyorsa `AppContextSwitchOverrides` , yeni değer şöyle bir değer özniteliğiyle birleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="6d5e5-109">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the value attribute like this:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="6d5e5-110">Name</span><span class="sxs-lookup"><span data-stu-id="6d5e5-110">Name</span></span>    | <span data-ttu-id="6d5e5-111">Değer</span><span class="sxs-lookup"><span data-stu-id="6d5e5-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6d5e5-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6d5e5-112">Scope</span></span>   | <span data-ttu-id="6d5e5-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="6d5e5-113">Minor</span></span>       |
| <span data-ttu-id="6d5e5-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6d5e5-114">Version</span></span> | <span data-ttu-id="6d5e5-115">4.6</span><span class="sxs-lookup"><span data-stu-id="6d5e5-115">4.6</span></span>         |
| <span data-ttu-id="6d5e5-116">Tür</span><span class="sxs-lookup"><span data-stu-id="6d5e5-116">Type</span></span>    | <span data-ttu-id="6d5e5-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="6d5e5-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6d5e5-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6d5e5-118">Affected APIs</span></span>

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
