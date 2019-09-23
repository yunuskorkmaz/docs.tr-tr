---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181734"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.EnableVisualStyleValidation` Uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, `Switch.System.Windows.Forms.EnableVisualStyleValidation` uyumluluk anahtarı bir uygulamanın sayısal biçimde sağlanan görsel stillerin doğrulanmasını geri açmasına izin verilir. 

.NET Core 'da, `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
