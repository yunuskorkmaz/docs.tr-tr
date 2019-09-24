---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217033"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont`değiştirme`Segoe UI 9pt`

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özelliği olarak `Microsoft Sans Serif 8pt`ayarlanmıştır. Aşağıdaki şekilde varsayılan yazı tipini kullanan bir pencere gösterilmektedir.

![.NET Framework 'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

.NET Core 'ta .NET Core 3,0 ile başlayarak, `Segoe UI 9pt` (aynı yazı tipi) olarak <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>ayarlanır. Bu değişikliğin sonucunda, form ve denetimler yeni varsayılan yazı tipinin daha büyük boyutu için% 27 daha büyük bir hesaba sahip olacaktır. Örneğin:

![Varsayılan denetim yazı tipi-.NET Core 'da](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Bu değişiklik [WINDOWS UX kılavuzlarıyla](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors)hizalanmaya çalışıldı.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Form ve denetimlerin boyutundaki değişiklik nedeniyle uygulamanızın doğru şekilde işlediğinden emin olun.

Özgün yazı tipini sürdürmek için formunuzun varsayılan yazı tipini olarak `Microsoft Sans Serif 8pt`ayarlayın. Örneğin:

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Kategori

- Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
