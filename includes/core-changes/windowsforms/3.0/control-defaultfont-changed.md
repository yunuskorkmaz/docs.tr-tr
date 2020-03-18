---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937115"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Varsayılan denetim yazı tipi Segoe UI 9 pt olarak değiştirildi

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework'de <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özellik `Microsoft Sans Serif 8 pt`. Aşağıdaki resimde varsayılan yazı tipini kullanan bir pencere gösterilmektedir.

![.NET Framework'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

.NET Core 3.0'dan başlayarak varsayılan `Segoe UI 9 pt` yazı tipi <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>(aynı yazı tipi) olarak ayarlanır. Bu değişikliğin bir sonucu olarak, formlar ve denetimler, yeni varsayılan yazı tipinin daha büyük boyutunu hesaba katmak için yaklaşık %27 daha büyük boyutlandırılır. Örnek:

![.NET Core'da varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Bu [değişiklik, Windows kullanıcı deneyimi (UX) yönergeleriile](/windows/win32/uxguide/vis-fonts#fonts-and-colors)uyumlu olarak yapılmıştır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Formların ve denetimlerin boyutundaki değişiklik nedeniyle, uygulamanızın doğru şekilde işlemesini sağlayın.

Özgün yazı tipini korumak için formunuzun `Microsoft Sans Serif 8 pt`varsayılan yazı tipini . Örnek:

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
