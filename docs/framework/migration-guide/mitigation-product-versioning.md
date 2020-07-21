---
title: 'Azaltma: Ürün Sürümü Oluşturma'
description: Bu makalede, önceki sürümlerden .NET Framework 4,6 ve üzeri ürün sürümü oluşturma işlemlerinin nasıl değiştiği hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475404"
---
# <a name="mitigation-product-versioning"></a>Azaltma: Ürün Sürümü Oluşturma

.NET Framework 4,6 ve üzeri sürümlerde, ürün sürümü oluşturma işlemi önceki .NET Framework sürümlerinden (.NET Framework 4, 4,5, 4.5.1 ve 4.5.2) değiştirilmiştir.

## <a name="product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri

Ayrıntılı değişiklikler aşağıda verilmiştir:

- Anahtardaki girdinin değeri, `Version` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` `4.6.` .NET Framework 4,6 ve noktası sürümleri için *xxxxx* , `4.7.` .NET Framework 4,7 için *xxxxx* olarak değiştirilmiştir. .NET Framework 4,5, 4.5.1 ve 4.5.2 ' de, `4.5.` *xxxxx*biçiminde vardı.

- .NET Framework dosyaları için dosya ve ürün sürümü oluşturma, `4.0.30319.x` `4.6.X.0` .NET Framework 4,6 ve noktası sürümleri için ve `4.7.X.0` .NET Framework 4,7 ve noktası sürümleri için için önceki sürüm oluşturma düzeninden değiştirilmiştir. Bir dosyaya sağ tıkladıktan sonra dosyanın **özelliklerini** görüntülerken bu yeni değerleri görebilirsiniz.

- <xref:System.Reflection.AssemblyFileVersionAttribute> <xref:System.Reflection.AssemblyInformationalVersionAttribute> Yönetilen derlemelerin ve özniteliklerinin <xref:System.Version> `4.6.X.0` .NET Framework 4,6 ve nokta sürümleri için ve .NET Framework 4,7 için biçimde değerleri vardır `4.7.X.0` .

- .NET Framework 4,6 ' den başlayarak, <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği sabit sürüm dizesini döndürür `4.0.30319.42000` . .NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini `4.0.30319.xxxxx` `xxxxx` 42000 ' den daha düşük olan biçimde döndürür (örneğin, "4.0.30319.18010"). Özellik üzerinde herhangi bir yeni bağımlılığı alan uygulama kodunu önermiyoruz <xref:System.Environment.Version%2A?displayProperty=nameWithType> .

### <a name="handling-the-product-versioning-changes"></a>Ürün sürümü oluşturma değişikliklerini işleme

Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:

- .NET Framework çalışma zamanı sürümünü algılamak için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).

- .NET Framework için yükleme yolunu öğrenmek için, `InstallPath` anahtardaki girdinin değerini kullanın `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` .

  > [!IMPORTANT]
  > Alt anahtar adı `NET Framework Setup` değil, `.NET Framework Setup` .

- .NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemini çağırın.

- CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemini çağırın.   .NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2 ve 4,7) için, dizeyi döndürür `v4.0.30319` .

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
