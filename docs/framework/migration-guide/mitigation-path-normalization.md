---
title: 'Azaltma: Yolu normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36433dcce1e47b329f5407e86ce3923a44cb6444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-path-normalization"></a>Azaltma: Yolu normalleştirme
Hedef uygulamalarla başlangıç [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], .NET Framework'teki yolu normalleştirme değişti.  
  
## <a name="what-is-path-normalization"></a>Yol normalleştirme nedir?  
 Bir yol normalleştirme bir yol veya dosya tanımlar ve böylece geçerli bir yol hedef işletim sisteminde uyacağını dizesini değiştirmeyi içerir. Normalleştirme genellikle içerir:  
  
-   Bileşen ve dizin ayırıcı standart hale getirme.  
  
-   Geçerli dizine göreli bir yol uygulanıyor.  
  
-   Göreli directory değerlendirme (`.`) ya da üst dizini (`..`) bir yolda.  
  
-   Kırpma karakterleri belirtilmiş.  
  
## <a name="the-changes"></a>Değişiklikleri  
 Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], yol normalleştirme aşağıdaki yollarla değişti:  
  
-   İşletim sistemi için çalışma zamanı erteler [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) yolları normalleştirmek için işlevi.  
  
-   Normalleştirme artık dizin Segment (örneğin, bir dizin adının sonunda boşluk) sonuna kırpma içerir.  
  
-   Tam güven yolu sözdiziminde cihaz için destek dahil olmak üzere `\\.\` ve mscorlib.dll, g/ç API'leri dosyasında `\\?\`.  
  
-   Çalışma zamanı aygıt sözdizimi yolları doğrulamaz.  
  
-   Alternatif veri akışları erişmek için cihaz sözdizimi kullanımı desteklenir.  
  
## <a name="impact"></a>Etki  
 Hedef uygulamalar için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikleri varsayılan olarak açıktır. Daha önce erişilemez yollara erişmek yöntemler verirken performansı.  
  
 Hedef uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümleri ancak olan çalışırken [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikten etkilenmez.  
  
## <a name="mitigation"></a>Azaltma  
 Hedef uygulamaları [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra dışında bu değişikliği kabul ve eski normalleştirme aşağıdakileri ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Hedef uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya önceki ancak üzerinde çalışan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama bölümü. yapılandırma dosyası:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
