---
title: 'Azaltma: Yol normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa31641cc325f15b9afe677038deb33c57e77fd1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508819"
---
# <a name="mitigation-path-normalization"></a>Azaltma: Yol normalleştirme
Hedef uygulama ile başlangıç [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], .NET Framework'teki yolu normalleştirme değişti.  
  
## <a name="what-is-path-normalization"></a>Yol normalleştirme nedir?  
 Bir yol normalleştirme, böylece geçerli bir yol hedef işletim sisteminde uyan bir yol veya dosya tanımlayan dize değiştirme içerir. Normalleştirme genellikle içerir:  
  
-   Bileşen ve dizin ayırıcı standart hale getirme.  
  
-   Geçerli dizine göreli bir yol uygulanıyor.  
  
-   Göreli dizini değerlendirme (`.`) veya bir üst dizin (`..`) bir yolda.  
  
-   Karakterleri kırpma belirtilmiş.  
  
## <a name="the-changes"></a>Değişiklikleri  
 Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], yol normalleştirme aşağıdaki yollarla değişmiştir:  
  
-   İşletim sistemi için çalışma zamanı erteler [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) yolları'leri normalleştirmek için işlevi.  
  
-   Artık normalleştirme directory Segment (örneğin, bir dizin adı, sonunda boşluk) sonuna kırpma içerir.  
  
-   Cihaz yolu sözdizimi tam güven için destek dahil olmak üzere `\\.\` ve dosya g/ç API'leri mscorlib.dll için `\\?\`.  
  
-   Çalışma zamanı, cihaz sözdizimi yolları doğrulamaz.  
  
-   Alternatif veri akışları erişmek için cihaz sözdizimi desteklenmiyor.  
  
## <a name="impact"></a>Etki  
 Hedefleyen uygulamalar için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikleri varsayılan olarak etkindir. Daha önce erişilemeyen yolları erişmek yöntemleri sağlarken performansı.  
  
 Hedefleyen uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümleri ancak bunlar çalışırken [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikten etkilenmez.  
  
## <a name="mitigation"></a>Azaltma  
 Hedefleyen uygulamaları [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra dışında bu değişikliği kabul ve eski normalleştirme aşağıdakileri ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyası bölümünü:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Hedefleyen uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya önceki ancak üzerinde çalışan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama bölümü. yapılandırma dosyası:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
