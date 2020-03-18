---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937071"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>UseLegacyImages uyumluluk anahtarı desteklenmiyor

.NET Framework 4.8'de tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.8'den `Switch.System.Windows.Forms.UseLegacyImages` başlayarak, uyumluluk anahtarı yüksek DPI ortamlarında ClickOnce senaryolarında olası görüntü ölçekleme sorunlarını ele aldı. `true`Ayarlandığında, anahtar, ölçeği %100'den büyük olan yüksek DPI ekranlarda eski görüntü ölçeklendirmesini geri yüklemesine olanak tanır. Daha fazla bilgi için github'daki [.NET Framework 4.8 Yayın Notları'na](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) bakın.

.NET Core'da `Switch.System.Windows.Forms.UseLegacyImages` anahtar desteklenmez.

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
