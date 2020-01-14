---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937115"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Varsayılan denetim yazı tipi Segoe UI 9 nk olarak değiştirildi

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> özelliği `Microsoft Sans Serif 8 pt`olarak ayarlanmıştır. Aşağıdaki görüntüde varsayılan yazı tipi kullanılan bir pencere gösterilmektedir.

![.NET Framework 'de varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

.NET Core 3,0 ' den başlayarak, varsayılan yazı tipi `Segoe UI 9 pt` (<xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>ile aynı yazı tipi) olarak ayarlanmıştır. Bu değişikliğin sonucu olarak, form ve denetimler yeni varsayılan yazı tipinin daha büyük boyutu için %27 daha büyük hesaba göre boyutlandırılır. Örneğin:

![.NET Core 'da varsayılan denetim yazı tipi](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Bu değişiklik [Windows Kullanıcı deneyimi (UX) yönergelerine](/windows/win32/uxguide/vis-fonts#fonts-and-colors)göre hizalanmaya çalışıldı.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Form ve denetimlerin boyutundaki değişiklik nedeniyle uygulamanızın doğru şekilde işlediğinden emin olun.

Özgün yazı tipini sürdürmek için, formunuzun varsayılan yazı tipini `Microsoft Sans Serif 8 pt`olarak ayarlayın. Örneğin:

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
