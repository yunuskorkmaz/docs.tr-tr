---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937069"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.EnableVisualStyleValidation` uyumluluk anahtarı .NET Core 3,0 üzerinde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, `Switch.System.Windows.Forms.EnableVisualStyleValidation` uyumluluk anahtarı bir uygulamanın sayısal bir biçimde sağlanan görsel stillerin doğrulanmasını geri açmasına izin verilir.

.NET Core 'da `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtarı desteklenmez.

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
