---
title: "UI Otomasyonu Değiştirme Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 73a1182adad742f1cb53b809ae07d78d1ec27cd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IToggleProvider>, yöntemleri ve özellikleri hakkındaki bilgileri de dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TogglePattern> Denetim düzeni döngüsü durumları bir dizi ile ve bir durum kez ayarlandıktan sonra korumak denetimleri desteklemek için kullanılır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 İki durumlu düğme denetim düzeni uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Düğmeler, araç çubuğu düğmeleri ve köprüleri gibi etkinleştirildiğinde durumu bulundurmayan denetimleri uygulanmalı <xref:System.Windows.Automation.Provider.IInvokeProvider> yerine.  
  
-   Bir denetim dolaşma gerekir, <xref:System.Windows.Automation.ToggleState> aşağıdaki sırayla: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> ve destekleniyorsa, <xref:System.Windows.Automation.ToggleState.Indeterminate>.  
  
-   <xref:System.Windows.Automation.TogglePattern>üç durumlu CheckBox doğrudan ayarını kendi uygun dönüşüm olmadan çevreleyen sorunları nedeniyle SetState(newState) yöntem sağlamaz <xref:System.Windows.Automation.ToggleState> dizisi.  
  
-   RadioButton denetimi uygulamayan <xref:System.Windows.Automation.Provider.IToggleProvider>, kendi geçerli durumları arasında geçiş yapma özelliğine sahip olmadığından.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>Gerekli üyeleri IToggleProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Özellik|Yok.|  
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim düzeni ilişkili hiçbir özel durum vardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
