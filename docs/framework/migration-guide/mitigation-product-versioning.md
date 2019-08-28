---
title: Mayı Ürün sürümü oluşturma
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f6016fc43700fda36c6d94408019d25f89bb36b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044204"
---
# <a name="mitigation-product-versioning"></a>Mayı Ürün sürümü oluşturma

.NET Framework 4,6 ve üzeri sürümlerde, ürün sürümü oluşturma işlemi önceki .NET Framework sürümlerinden (.NET Framework 4, 4,5, 4.5.1 ve 4.5.2) değiştirilmiştir.

## <a name="product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri

Ayrıntılı değişiklikler aşağıda verilmiştir:

- `Version` `4.6.` `4.7.` Anahtardaki girdinin değeri, .NET Framework 4,6 ve noktası sürümleri için xxxxx, .NET Framework 4,7 için xxxxx olarak değiştirilmiştir. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` .NET Framework 4,5, 4.5.1 ve 4.5.2 ' de, `4.5.` *xxxxx*biçiminde vardı.

- .NET Framework dosyaları için dosya ve ürün sürümü oluşturma, .NET Framework 4,6 ve `4.0.30319.x` `4.7.X.0` noktası sürümleri için ve .NET Framework `4.6.X.0` 4,7 ve noktası sürümleri için için önceki sürüm oluşturma düzeninden değiştirilmiştir. Bir dosyaya sağ tıkladıktan sonra dosyanın **özelliklerini** görüntülerken bu yeni değerleri görebilirsiniz.

- <xref:System.Version> `4.7.X.0` `4.6.X.0` Yönetilen derlemelerin <xref:System.Reflection.AssemblyInformationalVersionAttribute> ve özniteliklerinin .NET Framework 4,6 ve nokta sürümleri için ve .NET Framework 4,7 için biçimde değerleri vardır. <xref:System.Reflection.AssemblyFileVersionAttribute>

- .NET Framework 4,6 ' den başlayarak, <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği sabit sürüm dizesini `4.0.30319.42000`döndürür. .NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini 42000 ' den daha düşük `4.0.30319.xxxxx` `xxxxx` olan biçimde döndürür (örneğin, "4.0.30319.18010"). <xref:System.Environment.Version%2A?displayProperty=nameWithType> Özellik üzerinde herhangi bir yeni bağımlılığı alan uygulama kodunu önermiyoruz.

### <a name="handling-the-product-versioning-changes"></a>Ürün sürümü oluşturma değişikliklerini işleme

Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:

- .NET Framework çalışma zamanı sürümünü algılamak için bkz [. nasıl yapılır: Hangi .NET Framework sürümlerinin yükleneceğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)saptayın.

- .NET Framework için yükleme yolunu öğrenmek için, `InstallPath` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtardaki girdinin değerini kullanın.

  > [!IMPORTANT]
  > Alt anahtar adı `NET Framework Setup`değil `.NET Framework Setup`,.

- .NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemini çağırın.

- CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemini çağırın.   .NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2 ve 4,7) için, dizeyi `v4.0.30319`döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
