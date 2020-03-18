---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937069"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>EtkinleştirVisualStyleValidation uyumluluk anahtarı desteklenmiyor

Uyumluluk `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtarı .NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework'de `Switch.System.Windows.Forms.EnableVisualStyleValidation` uyumluluk anahtarı, bir uygulamanın sayısal biçimde sağlanan görsel stillerin doğrulanmasını devre dışı bırakmasına olanak sağladı.

.NET Core'da `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
