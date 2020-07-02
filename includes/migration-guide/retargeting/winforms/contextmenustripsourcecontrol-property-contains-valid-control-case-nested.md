---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614884"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="30599-101">ContextMenuStrip. SourceControl özelliği, iç içe ToolStripMenuItems durumunda geçerli bir denetim içeriyor</span><span class="sxs-lookup"><span data-stu-id="30599-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="30599-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30599-102">Details</span></span>

<span data-ttu-id="30599-103">.NET Framework 4.7.1 ve önceki sürümlerde <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliği, Kullanıcı menüyü iç içe geçmiş denetimlerden açtığında yanlış bir değer döndürür <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="30599-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="30599-104">.NET Framework 4.7.2 ve sonrasında, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> özelliği her zaman gerçek kaynak denetimine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="30599-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="30599-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="30599-105">Suggestion</span></span>

<span data-ttu-id="30599-106">**Bu değişiklikleri kabul etme veya devre dışı bırakma** Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30599-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="30599-107">Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="30599-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="30599-108">.NET Framework 4.7.2 ' i hedefliyor.</span><span class="sxs-lookup"><span data-stu-id="30599-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="30599-109">Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="30599-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="30599-110">Aşağıdaki örnekte gösterildiği gibi, .NET Framework 4.7.1 veya daha önceki bir sürümü hedefler ve eski erişilebilirlik davranışlarından yararlanarak, aşağıdaki [AppContext anahtarını](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` app.config dosyasının bölümüne ekleyerek ve öğesini olarak ayarlayarak eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .</span><span class="sxs-lookup"><span data-stu-id="30599-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="30599-111">.NET Framework 4.7.2 veya üstünü hedefleyen ve eski davranışı korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski kaynak denetimi değerinin kullanımını kabul edebilir `true` .</span><span class="sxs-lookup"><span data-stu-id="30599-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="30599-112">Name</span><span class="sxs-lookup"><span data-stu-id="30599-112">Name</span></span>    | <span data-ttu-id="30599-113">Değer</span><span class="sxs-lookup"><span data-stu-id="30599-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="30599-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="30599-114">Scope</span></span>   | <span data-ttu-id="30599-115">Edge</span><span class="sxs-lookup"><span data-stu-id="30599-115">Edge</span></span>        |
| <span data-ttu-id="30599-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="30599-116">Version</span></span> | <span data-ttu-id="30599-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="30599-117">4.7.2</span></span>       |
| <span data-ttu-id="30599-118">Tür</span><span class="sxs-lookup"><span data-stu-id="30599-118">Type</span></span>    | <span data-ttu-id="30599-119">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="30599-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="30599-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="30599-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
