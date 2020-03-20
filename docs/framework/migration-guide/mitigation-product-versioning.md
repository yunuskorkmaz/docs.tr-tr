---
title: 'Azaltma: Ürün Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457804"
---
# <a name="mitigation-product-versioning"></a>Azaltma: Ürün Sürümü Oluşturma

.NET Framework 4.6 ve sonraki sürümlerde, ürün sürümü .NET Framework'ün önceki sürümlerinden (.NET Framework 4, 4.5, 4.5.1 ve 4.5.2) değişmiştir.

## <a name="product-versioning-changes"></a>Ürün sürüm değişiklikleri

Ayrıntılı değişiklikler şunlardır:

- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` Anahtardaki `Version` girişin değeri .NET `4.6.`Framework 4.6 ve onun puan sürümleri için *xxxxx* ve `4.7.`.NET Framework 4.7 için *xxxxx* olarak değiştirildi. .NET Framework 4.5, 4.5.1 ve 4.5.2,, `4.5.`bu biçimi *xxxxx*vardı.

- .NET Framework dosyalarının dosya ve ürün sürümü, .NET `4.0.30319.x` Framework `4.6.X.0` 4.6 ve onun nokta sürümleri için `4.7.X.0` önceki sürüm şemasından ,.NET Framework 4.7 ve puan sürümlerine dönüşmüştür. Bir dosyaya sağ tıkladıktan sonra dosyanın **Özelliklerini** görüntülediğinizde bu yeni değerleri görebilirsiniz.

- Yönetilen <xref:System.Reflection.AssemblyFileVersionAttribute> <xref:System.Reflection.AssemblyInformationalVersionAttribute> derlemelerin öznitelikleri <xref:System.Version> ,NET Framework `4.6.X.0` 4.6 ve onun nokta sürümleri ve `4.7.X.0` .NET Framework 4.7 için formda değerlere sahiptir.

- .NET Framework 4.6 ile <xref:System.Environment.Version%2A?displayProperty=nameWithType> başlayarak, özellik `4.0.30319.42000`sabit sürüm dizesini döndürür. .NET Framework 4, 4.5, 4.5.1 ve 4.5.2'de sürüm dizelerini 42000'den az olan `4.0.30319.xxxxx` `xxxxx` biçimde döndürür (örneğin, "4.0.30319.18010"). Uygulama kodunun özelliğe yeni bir bağımlılık uygulamanızı önermediğimizi <xref:System.Environment.Version%2A?displayProperty=nameWithType> unutmayın.

### <a name="handling-the-product-versioning-changes"></a>Ürün sürüm değişikliklerini işleme

Genel olarak, uygulamalar .NET Framework'ün çalışma zamanı sürümü ve yükleme dizini gibi şeyleri algılamak için önerilen tekniklere bağlı olmalıdır:

- .NET Framework'ün çalışma zamanı sürümünü algılamak için [bkz: Hangi .NET Framework Sürümlerinin Yüklü olduğunu belirleyin.](how-to-determine-which-versions-are-installed.md)

- .NET Framework için yükleme yolunu belirlemek `InstallPath` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` için, anahtardaki giriş değerini kullanın.

  > [!IMPORTANT]
  > Alt anahtar adı `NET Framework Setup`, `.NET Framework Setup`değil.

- .NET Framework ortak dil çalışma zamanına giden dizin <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yolunu belirlemek için yöntemi arayın.

- CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemi arayın.   .NET Framework 4 ve onun nokta sürümleri için (.NET Framework 4.5, 4.5.1, 4.5.2 ve .NET Framework 4.6, 4.6.1, `v4.0.30319`4.6.2 ve 4.7) dizesini döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
