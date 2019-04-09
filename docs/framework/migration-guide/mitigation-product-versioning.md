---
title: 'Azaltma: Ürün sürümü oluşturma'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b435c6050cbb73abab3cb5980632be55dd08d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118020"
---
# <a name="mitigation-product-versioning"></a>Azaltma: Ürün sürümü oluşturma
İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve ürün sürümü oluşturma (.NET Framework 4, 4.5, 4.5.1 ve 4.5.2'yi) .NET Framework'ün önceki sürümlerinden daha sonra değişti.  
  
## <a name="product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri  
 Ayrıntılı değişiklikler şunlardır:  
  
-   Değerini `Version` girişi `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarı değişen `4.6.` *xxxxx* .NET Framework 4.6 ve onun nokta sürümleri ve için `4.7.` *xxxxx* için. NET Framework 4.7. İsteğe bağlı olarak .NET Framework 4.5, 4.5.1 ve 4.5.2'yi, formatına sahip `4.5.` *xxxxx*.  
  
-   .NET Framework dosyalar için dosya ve ürün sürümü oluşturma önceki sürüm oluşturma düzeni değişti `4.0.30319.x` için `4.6.X.0` .NET Framework 4.6 ve onun nokta sürümleri ve için `4.7.X.0` .NET Framework 4.7 ve onun nokta sürümleri. Dosyanın görüntülediğinizde, bu yeni değerleri görebilirsiniz **özellikleri** bir dosyaya sağ tıklayıp sonra.  
  
-   <xref:System.Reflection.AssemblyFileVersionAttribute> Ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> Yönetilen derlemeler için öznitelikleri <xref:System.Version> ve formdaki değerler `4.6.X.0` .NET Framework 4.6 ve onun nokta sürümleri ve `4.7.X.0` için .NET Framework 4.7.  
  
-   İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 ve 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> özellik sabit sürüm dizesi döndürür `4.0.30319.42000`. İsteğe bağlı olarak .NET Framework 4, 4.5, 4.5.1 ve 4.5.2'yi, sürüm dizeleri biçimde döndürür `4.0.30319.xxxxx` (örneğin, "4.0.30319.18010"). Uygulama kodu herhangi bir yeni bağımlılık almayı önermiyoruz Not <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="handling-the-product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri işleme  
 Genel olarak, uygulamaların çalışma zamanı sürümü, .NET Framework ve yükleme dizini gibi şeyler saptamak için önerilen teknikleri bağımlı:  
  
-   .NET Framework'ün çalışma zamanı sürümü algılamak için bkz: [nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
-   .NET Framework yükleme yolunu belirlemek için değerini kullanın. `InstallPath` girişi `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarı.  
  
    > [!IMPORTANT]
    >  Alt anahtar adı `NET Framework Setup`değil `.NET Framework Setup`.  
  
-   .NET Framework ortak dil çalışma zamanı dizin yolu belirlemek için çağrı <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemi.  
  
-   CLR sürümünü almak için arama <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemi.   .NET Framework 4 ve onun nokta sürümleri (.NET Framework 4.5, 4.5.1, 4.5.2 ve [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 ve 4.7), bir dize döndürür `v4.0.30319`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
