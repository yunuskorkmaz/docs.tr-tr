---
ms.openlocfilehash: 02dbf5ccca97f5e7d2e1fada39bdf601cf37906f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119361"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="b0336-101">`Control.DefaultFont`değiştirme`Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="b0336-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span> 

#### <a name="change-description"></a><span data-ttu-id="b0336-102">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b0336-102">Change description</span></span>

<span data-ttu-id="b0336-103">.NET Framework, <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özelliği olarak `Microsoft Sans Serif 8pt`ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0336-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="b0336-104">Aşağıdaki şekilde varsayılan yazı tipini kullanan bir pencere gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0336-104">The following figure shows a window that uses the default font.</span></span>

![.NET Framework 'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="b0336-106">.NET Core 'ta .NET Core 3,0 ile başlayarak, `Segoe UI 9pt` (aynı yazı tipi) olarak <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b0336-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="b0336-107">Bu değişikliğin sonucunda, form ve denetimler yeni varsayılan yazı tipinin daha büyük boyutu için% 27 daha büyük bir hesaba sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b0336-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="b0336-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0336-108">For example:</span></span>

![Varsayılan denetim yazı tipi-.NET Core 'da](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="b0336-110">Bu değişiklik [WINDOWS UX kılavuzlarıyla](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors)hizalanmaya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="b0336-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0336-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b0336-111">Version introduced</span></span>

<span data-ttu-id="b0336-112">3.0</span><span class="sxs-lookup"><span data-stu-id="b0336-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0336-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b0336-113">Recommended action</span></span>

<span data-ttu-id="b0336-114">Form ve denetimlerin boyutundaki değişiklik nedeniyle uygulamanızın doğru şekilde işlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b0336-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="b0336-115">Özgün yazı tipini sürdürmek için formunuzun varsayılan yazı tipini olarak `Microsoft Sans Serif 8pt`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b0336-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="b0336-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0336-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="b0336-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="b0336-117">Category</span></span>

- <span data-ttu-id="b0336-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0336-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0336-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b0336-119">Affected APIs</span></span>

<span data-ttu-id="b0336-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0336-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->