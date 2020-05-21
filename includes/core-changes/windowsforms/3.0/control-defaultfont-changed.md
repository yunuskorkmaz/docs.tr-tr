---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721562"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Varsayılan denetim yazı tipi Segoe UI 9 nk olarak değiştirildi

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özelliği olarak ayarlanmıştır `Microsoft Sans Serif 8 pt` . Aşağıdaki görüntüde varsayılan yazı tipi kullanılan bir pencere gösterilmektedir.

![.NET Framework 'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

.NET Core 3,0 ' den başlayarak, varsayılan yazı tipi `Segoe UI 9 pt` (ile aynı yazı tipi) olarak ayarlanır <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> . Bu değişikliğin sonucu olarak, form ve denetimler yeni varsayılan yazı tipinin daha büyük boyutu için %27 daha büyük hesaba göre boyutlandırılır. Örneğin:

![.NET Core 'da varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Bu değişiklik [Windows Kullanıcı deneyimi (UX) yönergelerine](/windows/win32/uxguide/vis-fonts#fonts-and-colors)göre hizalanmaya çalışıldı.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Form ve denetimlerin boyutundaki değişiklik nedeniyle uygulamanızın doğru şekilde işlediğinden emin olun.

Özgün yazı tipini sürdürmek için formunuzun varsayılan yazı tipini olarak ayarlayın `Microsoft Sans Serif 8 pt` . Örneğin:

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

#### Affected APIs

- Not detectable via API analysis

-->
