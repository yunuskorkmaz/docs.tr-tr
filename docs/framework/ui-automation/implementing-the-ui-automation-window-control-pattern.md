---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180040"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI Otomasyonu Pencere Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.IWindowProvider>olaylar hakkında <xref:System.Windows.Automation.WindowPattern> bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.WindowPattern> deseni, geleneksel grafik kullanıcı arabirimi (GUI) içinde temel pencere tabanlı işlevsellik sağlayan denetimleri desteklemek için kullanılır. Bu denetim deseni uygulaması gereken denetimlere örnek olarak üst düzey uygulama pencereleri, çoklu belge arabirimi (MDI) alt pencereleri, yeniden boyutlandırılabilir bölme denetimleri, modal iletişim kutuları ve balon yardım pencereleri verilebilir.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Pencere denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:  
  
- UI Automation kullanarak hem pencere boyutunu hem de ekran konumunu <xref:System.Windows.Automation.Provider.ITransformProvider> değiştirme yeteneğini <xref:System.Windows.Automation.Provider.IWindowProvider>desteklemek için, bir denetimin ek olarak uygulanması gerekir.  
  
- Denetimin taşınmasını, yeniden boyutlandırılmasını, en üst düzeye çıkarılmasını, en aza indirilmesini veya <xref:System.Windows.Automation.Provider.IWindowProvider>kapatılmasını sağlayan başlık çubukları ve başlık çubuğu öğeleri içeren denetimlerin uygulanması genellikle gereklidir.  
  
- Araç ucu açılır pencereleri ve açılan kutu veya menü açılır pencereleri <xref:System.Windows.Automation.Provider.IWindowProvider>gibi denetimler genellikle uygulanmaz.  
  
- Balon yardım pencereleri, pencere benzeri Kapat düğmesi nin sağlanmasıyla temel araç ucu açılır pencerelerinden ayırt edilir.  
  
- Bir uygulamaya özel özellik olduğundan ve tipik bir pencere davranışı olmadığı için tam ekran modu IWindowProvider tarafından desteklenmez.  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>IWindowProvider için Gerekli Üyeler  
 IWindowProvider arabirimi için aşağıdaki özellikler, yöntemler ve olaylar gereklidir.  
  
|Gerekli üye|Üye tipi|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Olay|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Olay|None|  
|<xref:System.Windows.Automation.WindowInteractionState>|Olay|Olduğu garanti edilmez<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - Denetim istenen davranışı desteklemediğinde.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - Parametre geçerli bir sayı olmadığında.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
