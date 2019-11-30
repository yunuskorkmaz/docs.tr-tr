---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644035"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. UseLegacyImages uyumluluk anahtarı desteklenmiyor

.NET Framework 4,8 ' de tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,8 ' den başlayarak, `Switch.System.Windows.Forms.UseLegacyImages` uyumluluğu anahtarı yüksek DPı ortamlarında ClickOnce senaryolarında olası görüntü ölçeklendirme sorunlarını çözmekteydi. `true`olarak ayarlandığında, anahtar, ölçek %100 ' den büyük olarak ayarlanan yüksek DPı ekranlarda kullanıcının eski görüntü ölçeklendirmesini geri yüklemesine izin verir. Daha fazla bilgi için bkz. GitHub üzerinde [.NET Framework 4,8 sürüm notları](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) .

.NET Core 'da `Switch.System.Windows.Forms.UseLegacyImages` anahtarı desteklenmez.

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
