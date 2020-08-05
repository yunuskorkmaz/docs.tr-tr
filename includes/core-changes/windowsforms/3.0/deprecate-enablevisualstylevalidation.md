---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556220"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.EnableVisualStyleValidation`Uyumluluk anahtarı .NET Core veya .net 5,0 ve sonraki sürümlerde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, `Switch.System.Windows.Forms.EnableVisualStyleValidation` Uyumluluk anahtarı bir uygulamanın sayısal biçimde sağlanan görsel stillerin doğrulanmasını geri açmasına izin verilir.

.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Hiçbiri

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
