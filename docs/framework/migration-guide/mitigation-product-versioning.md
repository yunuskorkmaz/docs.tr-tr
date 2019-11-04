---
title: 'Azaltma: Ürün Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457804"
---
# <a name="mitigation-product-versioning"></a>Azaltma: Ürün Sürümü Oluşturma

.NET Framework 4,6 ve üzeri sürümlerde, ürün sürümü oluşturma işlemi önceki .NET Framework sürümlerinden (.NET Framework 4, 4,5, 4.5.1 ve 4.5.2) değiştirilmiştir.

## <a name="product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri

Ayrıntılı değişiklikler aşağıda verilmiştir:

- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarındaki `Version` girdinin değeri .NET Framework 4,6 ve noktası sürümleri için `4.6.`*xxxxx* , `4.7.`4,7 için .NET Framework *xxxxx* olarak değiştirilmiştir. .NET Framework 4,5, 4.5.1 ve 4.5.2 `4.5.`*xxxxx*biçiminde vardı.

- .NET Framework dosyaları için dosya ve ürün sürümü oluşturma, .NET Framework 4,6 ve noktası sürümleri için `4.6.X.0` `4.0.30319.x` önceki sürüm oluşturma düzeninden değiştirilmiştir ve `4.7.X.0` 4,7 ve noktası sürümleri için .NET Framework. Bir dosyaya sağ tıkladıktan sonra dosyanın **özelliklerini** görüntülerken bu yeni değerleri görebilirsiniz.

- Yönetilen derlemeler için <xref:System.Reflection.AssemblyFileVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri, .NET Framework 4,6 ve noktası sürümleri için `4.6.X.0` ve `4.7.X.0` 4,7 .NET Framework için formda <xref:System.Version> değerlere sahiptir.

- .NET Framework 4,6 ' den itibaren <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği, `4.0.30319.42000`sabit sürüm dizesini döndürür. .NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini `xxxxx` 42000 ' den küçük olan `4.0.30319.xxxxx` biçiminde döndürür (örneğin, "4.0.30319.18010"). Uygulama kodunun <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği üzerinde herhangi bir yeni bağımlılığı alan önermediğine göz önünde bulunuyoruz.

### <a name="handling-the-product-versioning-changes"></a>Ürün sürümü oluşturma değişikliklerini işleme

Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:

- .NET Framework çalışma zamanı sürümünü algılamak için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).

- .NET Framework yükleme yolunu öğrenmek için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarındaki `InstallPath` girişinin değerini kullanın.

  > [!IMPORTANT]
  > Alt anahtar adı, `.NET Framework Setup`değil `NET Framework Setup`.

- .NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için, <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemini çağırın.

- CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemini çağırın.   .NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2 ve 4,7) için, `v4.0.30319`dize döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
