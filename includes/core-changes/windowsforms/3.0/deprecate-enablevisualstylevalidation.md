---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721663"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.EnableVisualStyleValidation`Uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, `Switch.System.Windows.Forms.EnableVisualStyleValidation` Uyumluluk anahtarı bir uygulamanın sayısal biçimde sağlanan görsel stillerin doğrulanmasını geri açmasına izin verilir.

.NET Core 'da, `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
