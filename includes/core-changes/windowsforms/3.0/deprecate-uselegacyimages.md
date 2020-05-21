---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721332"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>UseLegacyImages uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.UseLegacyImages`.NET Framework 4,8 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,8 ' den başlayarak, `Switch.System.Windows.Forms.UseLegacyImages` Uyumluluk anahtarı yüksek DPI ortamlarında ClickOnce senaryolarında olası görüntü ölçeklendirme sorunlarını çözmekteydi. Olarak ayarlandığında `true` , anahtar, ölçek %100 ' den büyük olarak ayarlanan yüksek DPI ekranlarda kullanıcının eski görüntü ölçeklendirmesini geri yüklemesine izin verir. Daha fazla bilgi için bkz. GitHub üzerinde [.NET Framework 4,8 sürüm notları](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) .

.NET Core 'da, `Switch.System.Windows.Forms.UseLegacyImages` anahtar desteklenmez.

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
