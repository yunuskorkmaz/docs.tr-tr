---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 9063146ac4bee750c4865787b7b44cea6354d30c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712360"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>UI Otomasyon MultipleView Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.MultipleViewPattern> Denetim düzeni sağlayın ve birden çok bilgi veya alt denetim aynı dizi temsillerini, arasında geçiş yapabilirsiniz denetimleri desteklemek için kullanılır.  
  
 Birden çok görünüm sunabilir denetimleri örnekler (da içeriğini küçük resimleri, kutucukları, simgeler veya ayrıntılar gösterebilir) liste görünümü [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikleri (pasta, çizgi, çubuk, hücre değerini bir formül ile), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belgeleri (normal, Web düzeni yazdırma düzeni, okuma düzeni, anahat) [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] (yıl, ay, hafta, gün), Takvim ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] css'li dış görünümler. Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her bir denetimin özgüdür.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Birden çok görünüm denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> Ayrıca, geçerli görünüm sağlayan bir denetimi farklıysa, geçerli görünüm yöneten bir kapsayıcıda uygulanmalıdır. Örneğin, görünüm denetimi için Windows Gezgini uygulamadan yönetilen Windows Explorer geçerli klasör içeriği için bir liste denetimini içerir.  
  
-   İçeriği sıralama mümkün olan denetimi birden çok görünüm desteklemek için dikkate alınmaz.  
  
-   Görünümler koleksiyonu örneklerinde aynı olmalıdır.  
  
-   Görünüm adları metin okuma, Braille ve okunabilir diğer uygulamalar için uygun olması gerekir.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Gerekli üyeleri IMultipleViewProvider için  
 Aşağıdaki özellikleri ve yöntemleri IMultipleViewProvider uygulamak için gereklidir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim düzeni ile ilişkili olay yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcı, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Zaman ya da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> veya <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> desteklenen görünümler koleksiyonunun bir üyesi olmayan bir parametre ile adlandırılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
