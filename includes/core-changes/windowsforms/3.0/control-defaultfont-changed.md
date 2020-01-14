---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937115"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="25180-101">Varsayılan denetim yazı tipi Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="25180-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="25180-102">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="25180-102">Change description</span></span>

<span data-ttu-id="25180-103">.NET Framework, <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özelliği `Microsoft Sans Serif 8 pt`olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="25180-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="25180-104">Aşağıdaki görüntüde varsayılan yazı tipi kullanılan bir pencere gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25180-104">The following image shows a window that uses the default font.</span></span>

![.NET Framework 'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="25180-106">.NET Core 3,0 ' den başlayarak, varsayılan yazı tipi `Segoe UI 9 pt` (<xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>ile aynı yazı tipi) olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="25180-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="25180-107">Bu değişikliğin sonucu olarak, form ve denetimler yeni varsayılan yazı tipinin daha büyük boyutu için %27 daha büyük hesaba göre boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="25180-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="25180-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="25180-108">For example:</span></span>

![.NET Core 'da varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="25180-110">Bu değişiklik [Windows Kullanıcı deneyimi (UX) yönergelerine](/windows/win32/uxguide/vis-fonts#fonts-and-colors)göre hizalanmaya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="25180-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="25180-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="25180-111">Version introduced</span></span>

<span data-ttu-id="25180-112">3.0</span><span class="sxs-lookup"><span data-stu-id="25180-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="25180-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="25180-113">Recommended action</span></span>

<span data-ttu-id="25180-114">Form ve denetimlerin boyutundaki değişiklik nedeniyle uygulamanızın doğru şekilde işlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="25180-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="25180-115">Özgün yazı tipini sürdürmek için, formunuzun varsayılan yazı tipini `Microsoft Sans Serif 8 pt`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="25180-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="25180-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="25180-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="25180-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="25180-117">Category</span></span>

- <span data-ttu-id="25180-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25180-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25180-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="25180-119">Affected APIs</span></span>

<span data-ttu-id="25180-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="25180-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
