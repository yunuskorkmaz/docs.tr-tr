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
manager: markl
ms.openlocfilehash: 73a484ea6165b4e38901630730c7ba985a5608ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI Otomasyonu Pencere Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IWindowProvider>, ilgili bilgiler dahil olmak üzere <xref:System.Windows.Automation.WindowPattern> özellikleri, yöntemleri ve olaylar. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.WindowPattern> Denetim düzeni içinde geleneksel Windows tabanlı temel işlevleri sağlayan denetimleri desteklemek için kullanılan [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Bu denetim düzeni uygulamalıdır denetimleri örnekleri arasında en üst düzey uygulama windows [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] alt öğe pencerelerini, yeniden boyutlandırılabilir bölünmüş bölmesi denetimlerinin, kalıcı iletişim kutuları ve balon windows yardımcı olur.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Pencere denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   UI Otomasyonu kullanarak konumu ekran ve her iki pencere boyutunu değiştirmek için yeteneğini desteklemek için bir denetim uygulamalıdır <xref:System.Windows.Automation.Provider.ITransformProvider> ek olarak <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Başlık çubukları ve taşınmasına izin denetimini değişirse ekranı, etkinleştirme başlık çubuğu öğeleri içeren denetimler küçültülebilir ya da kapalı uygulamak için genellikle gereken <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Araç İpucu açılır pencereleri ve birleşik giriş kutusu veya menü aşağı açılan listeler gibi denetimleri genellikle uygulamaz <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Balon Yardım windows temel araç ipucu pencerelere penceresi benzeri Kapat düğmesi sağlama tarafından ayrılır.  
  
-   Tam ekran modu özelliğe özgü olduğu gibi IWindowProvider tarafından desteklenmiyor uygulamaya ve tipik penceresi davranış değildir.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Gerekli üyeleri IWindowProvider için  
 Aşağıdaki özellikleri, yöntemleri ve olayları IWindowProvider arabirim için gereklidir.  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Olay|Yok.|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Olay|Yok.|  
|<xref:System.Windows.Automation.WindowInteractionState>|Olay|Olması garanti edilmez <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -Ne zaman bir denetim istenen davranışını desteklemez.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Zaman parametresi geçerli bir sayı değil.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
