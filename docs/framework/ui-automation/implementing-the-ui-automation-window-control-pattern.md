---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: ad2f84fbde512bb99b213bf3b97f2190091d8576
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042985"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI Otomasyonu Pencere Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.IWindowProvider> <xref:System.Windows.Automation.WindowPattern> bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.WindowPattern> Denetim stili, geleneksel bir grafik kullanıcı arabirimi (GUI) içinde temel pencere tabanlı işlevselliği sağlayan denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri, en üst düzey uygulama pencereleri, birden çok belge arabirimi (MDI) alt pencereleri, yeniden boyutlandırılabilir bölünmüş bölme denetimleri, kalıcı iletişim kutuları ve balon yardım pencereleri içerir.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Pencere denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- UI Otomasyonu kullanarak pencere boyutunu ve ekran konumunu değiştirme özelliğini desteklemek için, bir denetimin <xref:System.Windows.Automation.Provider.ITransformProvider> <xref:System.Windows.Automation.Provider.IWindowProvider>buna ek olarak uygulanması gerekir.  
  
- Denetimin taşınmasını, yeniden boyutlandırılması, büyütülmüş, küçültülmüş veya kapalı olmasını sağlayan başlık çubuklarını ve başlık çubuğu öğelerini içeren denetimler genellikle uygulamak <xref:System.Windows.Automation.Provider.IWindowProvider>için gereklidir.  
  
- Araç ipucu açılır pencereleri ve Birleşik giriş kutusu ya da menü açılır listeleri gibi denetimler genellikle uygulamaz <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Balon yardım pencereleri, bir pencere gibi Kapat düğmesinin sağlanması ile temel araç ipucu açılarından farklılaştırılabilir.  
  
- Tam ekran modu, bir uygulamaya özgü olan ve tipik bir pencere davranışı olmayan IWindowProvider tarafından desteklenmiyor.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>IWindowProvider için gerekli Üyeler  
 IWindowProvider arabirimi için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.  
  
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
|<xref:System.Windows.Automation.WindowInteractionState>|Olay|Garanti edilmez<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -Bir denetim istenen davranışı desteklemiyorsa.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Parametre geçerli bir sayı değil.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
