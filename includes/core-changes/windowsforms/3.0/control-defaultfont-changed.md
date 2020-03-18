---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937115"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="ca3a7-101">Varsayılan denetim yazı tipi Segoe UI 9 pt olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="ca3a7-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="ca3a7-102">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="ca3a7-102">Change description</span></span>

<span data-ttu-id="ca3a7-103">.NET Framework'de <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özellik `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="ca3a7-104">Aşağıdaki resimde varsayılan yazı tipini kullanan bir pencere gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-104">The following image shows a window that uses the default font.</span></span>

![.NET Framework'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="ca3a7-106">.NET Core 3.0'dan başlayarak varsayılan `Segoe UI 9 pt` yazı tipi <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>(aynı yazı tipi) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="ca3a7-107">Bu değişikliğin bir sonucu olarak, formlar ve denetimler, yeni varsayılan yazı tipinin daha büyük boyutunu hesaba katmak için yaklaşık %27 daha büyük boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="ca3a7-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ca3a7-108">For example:</span></span>

![.NET Core'da varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="ca3a7-110">Bu [değişiklik, Windows kullanıcı deneyimi (UX) yönergeleriile](/windows/win32/uxguide/vis-fonts#fonts-and-colors)uyumlu olarak yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ca3a7-111">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="ca3a7-111">Version introduced</span></span>

<span data-ttu-id="ca3a7-112">3,0</span><span class="sxs-lookup"><span data-stu-id="ca3a7-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ca3a7-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ca3a7-113">Recommended action</span></span>

<span data-ttu-id="ca3a7-114">Formların ve denetimlerin boyutundaki değişiklik nedeniyle, uygulamanızın doğru şekilde işlemesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="ca3a7-115">Özgün yazı tipini korumak için formunuzun `Microsoft Sans Serif 8 pt`varsayılan yazı tipini .</span><span class="sxs-lookup"><span data-stu-id="ca3a7-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="ca3a7-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ca3a7-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="ca3a7-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="ca3a7-117">Category</span></span>

- <span data-ttu-id="ca3a7-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca3a7-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca3a7-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ca3a7-119">Affected APIs</span></span>

<span data-ttu-id="ca3a7-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca3a7-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
