---
ms.openlocfilehash: 5529b8379c5cb9f1bc525e0c2340f6b885e35822
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606700"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="dab0c-101">ContextMenuStrip. SourceControl özelliği, iç içe ToolStripMenuItems durumunda geçerli bir denetim içeriyor</span><span class="sxs-lookup"><span data-stu-id="dab0c-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="dab0c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="dab0c-102">Details</span></span>

<span data-ttu-id="dab0c-103">.NET Framework 4.7.1 ve önceki sürümlerde <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliği, Kullanıcı menüyü iç içe geçmiş denetimlerden açtığında yanlış bir değer döndürür <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="dab0c-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="dab0c-104">.NET Framework 4.7.2 ve sonrasında, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> özelliği her zaman gerçek kaynak denetimine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dab0c-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dab0c-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="dab0c-105">Suggestion</span></span>

<span data-ttu-id="dab0c-106">**Bu değişiklikleri kabul etme veya devre dışı bırakma** Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dab0c-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="dab0c-107">Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="dab0c-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="dab0c-108">.NET Framework 4.7.2 ' i hedefliyor.</span><span class="sxs-lookup"><span data-stu-id="dab0c-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="dab0c-109">Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dab0c-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="dab0c-110">Aşağıdaki örnekte gösterildiği gibi, .NET Framework 4.7.1 veya daha önceki bir sürümü hedefler ve eski erişilebilirlik davranışlarından yararlanarak, aşağıdaki [AppContext anahtarını](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` app.config dosyasının bölümüne ekleyerek ve öğesini olarak ayarlayarak eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .</span><span class="sxs-lookup"><span data-stu-id="dab0c-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="dab0c-111">.NET Framework 4.7.2 veya üstünü hedefleyen ve eski davranışı korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski kaynak denetimi değerinin kullanımını kabul edebilir `true` .</span><span class="sxs-lookup"><span data-stu-id="dab0c-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="dab0c-112">Name</span><span class="sxs-lookup"><span data-stu-id="dab0c-112">Name</span></span>    | <span data-ttu-id="dab0c-113">Değer</span><span class="sxs-lookup"><span data-stu-id="dab0c-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dab0c-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="dab0c-114">Scope</span></span>   | <span data-ttu-id="dab0c-115">Edge</span><span class="sxs-lookup"><span data-stu-id="dab0c-115">Edge</span></span>        |
| <span data-ttu-id="dab0c-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dab0c-116">Version</span></span> | <span data-ttu-id="dab0c-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="dab0c-117">4.7.2</span></span>       |
| <span data-ttu-id="dab0c-118">Tür</span><span class="sxs-lookup"><span data-stu-id="dab0c-118">Type</span></span>    | <span data-ttu-id="dab0c-119">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="dab0c-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="dab0c-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="dab0c-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
