---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: e436a9505ea9ae770a748da244dd21ce63ad3464
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736987"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI Otomasyonu Pencere Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IWindowProvider>, hakkında bilgiler dahil olmak üzere <xref:System.Windows.Automation.WindowPattern> özellikleri, yöntemleri ve olayları. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.WindowPattern> Denetim düzeni geleneksel içinde pencere tabanlı temel işlevleri sağlayan denetimleri desteklemek için kullanılan [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Bu denetim düzeni uygulamalıdır denetimlerin örnekleri şunlardır en üst düzey uygulama windows [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] alt pencereler, yeniden boyutlandırılabilir bölünmüş bölme denetimleri, kalıcı iletişim kutuları ve balon windows Yardımı.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Pencere denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Her iki pencere boyutunu değiştirmek ve UI Otomasyonu kullanarak konumu ekran özelliği desteklemek için bir denetim uygulamalıdır <xref:System.Windows.Automation.Provider.ITransformProvider> ek olarak <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Başlık çubukları ve ekranı, taşınacak, Denetim değişirse etkinleştiren başlık çubuğu öğeleri içeren denetimler küçültülebilir ya da kapalı uygulamak için genellikle gereken <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Araç İpucu açılan pencereleri ve birleşik giriş kutusu veya menü açılan listeler gibi denetimler genellikle uygulamayın <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Balon Yardım windows penceresi benzeri Kapat düğmesi sağlayarak temel bir araç ipucu pencerelere ayrılır.  
  
-   Tam ekran modunda desteklenmeyen IWindowProvider tarafından özelliğe özgü olduğu gibi bir uygulamaya ve tipik pencere davranışını değil.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Gerekli üyeleri IWindowProvider için  
 Aşağıdaki özellikleri, yöntemleri ve olayları IWindowProvider arabirimi gerekli değildir.  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Olay|Hiçbiri|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Olay|Hiçbiri|  
|<xref:System.Windows.Automation.WindowInteractionState>|Olay|Olması garanti edilmez <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -Bir denetim, istenen davranışı desteklemez.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Parametresi geçerli bir sayı değil.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
