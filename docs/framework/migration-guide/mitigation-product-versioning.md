---
title: 'Azaltma: Ürün Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 483a6532ad62fb7e1561ac5cc4de37aeaaf45fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389411"
---
# <a name="mitigation-product-versioning"></a>Azaltma: Ürün Sürümü Oluşturma
İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve ürün sürümü oluşturma (.NET Framework 4, 4.5, 4.5.1 ve 4.5.2) .NET Framework'ün önceki sürümlerden daha sonra değişti.  
  
## <a name="product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri  
 Ayrıntılı değişiklikler şunlardır:  
  
-   Değeri `Version` girişi `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarı için değişti `4.6.` *xxxxx* .NET Framework 4.6 ve onun noktası serbest bırakır ve için `4.7.` *xxxxx* için. NET Framework 4.7. İsteğe bağlı olarak .NET Framework 4.5 ve 4.5.1 4.5.2, biçimi hatalıydı `4.5.` *xxxxx*.  
  
-   .NET Framework dosyalar için dosya ve ürün sürümü oluşturma önceki sürüm düzeninden değişti `4.0.30319.x` için `4.6.X.0` .NET Framework 4.6 ve onun noktası serbest bırakır ve için `4.7.X.0` .NET Framework 4.7 ve kendi noktası için serbest bırakır. Dosyanın görüntülediğinizde, bu yeni değerler görebilirsiniz **özellikleri** bir dosyaya sağ tıklatıp sonra.  
  
-   <xref:System.Reflection.AssemblyFileVersionAttribute> Ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> Yönetilen derlemeler için öznitelikleri <xref:System.Version> form değerleri `4.6.X.0` .NET Framework 4.6 ve onun noktası serbest bırakır ve `4.7.X.0` için .NET Framework 4.7.  
  
-   İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 ve 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür sabit sürüm dizesi `4.0.30319.42000`. İsteğe bağlı olarak .NET Framework 4, 4.5, 4.5.1 ve 4.5.2, sürüm dizelerini biçimde döndürür `4.0.30319.xxxxx` (örneğin, "4.0.30319.18010"). Yeni bir bağımlılık almayı uygulama kodu önermiyoruz Not <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="handling-the-product-versioning-changes"></a>Ürün sürümü oluşturma değişiklikleri işleme  
 Genel olarak, uygulamalar .NET Framework ve yükleme dizinini çalışma zamanı sürümü gibi şeyler saptamak için önerilen teknikleri bağlı:  
  
-   .NET Framework çalışma zamanı sürümü algılamak için bkz: [nasıl yapılır: belirlemek, .NET Framework sürümlerinin yüklendiğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
-   .NET Framework için yükleme yolu belirlemek için değerini kullanmak `InstallPath` girişi `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarı.  
  
    > [!IMPORTANT]
    >  Alt anahtar adı `NET Framework Setup`değil `.NET Framework Setup`.  
  
-   .NET Framework ortak dil çalışma zamanı dizin yolu belirlemek için arama <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemi.  
  
-   CLR sürümünü almak için arama <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemi.   .NET Framework 4 ve kendi noktası için serbest (.NET Framework 4.5, 4.5.1, 4.5.2 ve [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 ve 4.7), bir dize döndürür `v4.0.30319`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
 
