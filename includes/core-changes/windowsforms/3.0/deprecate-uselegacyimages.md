---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556227"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>UseLegacyImages uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.UseLegacyImages`.NET Framework 4,8 ' de tanıtılan uyumluluk anahtarı .NET Core veya .net 5,0 ve sonraki sürümlerde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,8 ' den başlayarak, `Switch.System.Windows.Forms.UseLegacyImages` Uyumluluk anahtarı yüksek DPI ortamlarında ClickOnce senaryolarında olası görüntü ölçeklendirme sorunlarını çözmekteydi. Olarak ayarlandığında `true` , anahtar, ölçek %100 ' den büyük olarak ayarlanan yüksek DPI ekranlarda kullanıcının eski görüntü ölçeklendirmesini geri yüklemesine izin verir. Daha fazla bilgi için bkz. GitHub üzerinde [.NET Framework 4,8 sürüm notları](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) .

.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.UseLegacyImages` anahtar desteklenmez.

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
