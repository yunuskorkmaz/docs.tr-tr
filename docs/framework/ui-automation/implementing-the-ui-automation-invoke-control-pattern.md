---
title: "UI Otomasyon Çağırma Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
caps.latest.revision: "31"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d40bc94887df604577c025181ae7f5f2776cdc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>UI Otomasyon Çağırma Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IInvokeProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.InvokePattern> Denetim düzeni değil etkinleştirildiğinde durumunu ancak bunun yerine başlatma korumak veya tek ve anlaşılır bir eylemi gerçekleştirmek denetimlerin desteklemek için kullanılır. Onay kutuları ve radyo düğmeleri gibi durumunu korumak denetimleri yerine uygulanmalı <xref:System.Windows.Automation.Provider.IToggleProvider> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider> sırasıyla. Çağır denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Çağır denetim düzeni uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Denetimleri uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider> başka bir denetim düzeni sağlayıcısı ile aynı davranışı açık değilse. Örneğin, varsa <xref:System.Windows.Automation.InvokePattern.Invoke%2A> yöntemi denetim üzerinde aynı eylemi gerçekleştirir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> yöntemi, Denetim uygulamaz <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Denetim harekete tıklatarak veya çift veya ENTER, önceden tanımlanmış klavye kısayolu veya alternatif bir bileşimi tuş vuruşları tuşuna basarak genellikle gerçekleştirilir.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>(olarak ilişkili eyleme taşıyan bir denetim yanıta) etkinleştirilmiş bir denetimi tetiklenir. Mümkünse, Olay denetimi eylemi tamamladıktan ve engellenmeden döndürülen sonra oluşmalıdır. Aşağıdaki senaryolarda Invoke isteği bakım önce Invoked olay gerçekleşti:  
  
    -   Bu olası veya eylem tamamlanana kadar beklemesini kullanışlı değildir.  
  
    -   Eylem kullanıcı etkileşimi gerektirir.  
  
    -   Eylem zaman alır ve önemli miktarda zaman engellemek çağıran istemci neden olur.  
  
-   Aracılığıyla denetimi çağırma önemli yan etkileri varsa, bu yan etkileri açılmamalıdır <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> özelliği. Örneğin, olsa bile <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> seçimi ile ilişkili değil <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> seçili hale başka bir denetim neden olabilir.  
  
-   Getirin (veya fare üzerinden) etkiler genellikle değil oluşturan bir Invoked olay. Ancak, vurgulu durumuna bağlı bir eylem (aksine, nedenini görsel bir efekt) gerçekleştirmek denetimlerin desteklemelidir <xref:System.Windows.Automation.InvokePattern> denetim düzeni.  
  
> [!NOTE]
>  Bu uygulama denetimi yalnızca fare ilgili yan etkisi sonucunda çağrılabilir varsa erişilebilirlik ile ilgili bir sorun olarak kabul edilir.  
  
-   Bir denetim çağırma öğeyi seçerek farklıdır. Ancak, denetimin bağlı olarak, çağırma yan etkisi olarak seçili hale öğesi neden olabilir. Örneğin, çağırma bir [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belge liste öğesini Belgelerim klasörünü hem öğesi seçer ve belge açılır.  
  
-   Bir öğenin kaldırılmasını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrılan hemen sonra ağacı. Olay geri çağırmasının tarafından sağlanan öğeden bilgilerini isteyen sonucunda başarısız olabilir. Önbelleğe alınan bilgileri önceden getirme önerilen geçici bir çözüm değildir.  
  
-   Denetimleri birden çok denetim düzenleri uygulayabilirsiniz. Örneğin, dolgu rengi denetiminde [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] araç uygulayan her ikisi de <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.ExpandCollapsePattern> denetim düzenleri. <xref:System.Windows.Automation.ExpandCollapsePattern>Menü kullanıma sunar ve <xref:System.Windows.Automation.InvokePattern> etkin seçimi seçilen renkle doldurur.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Gerekli üyeleri IInvokeProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|yöntemi|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>zaman uyumsuz bir çağrı ve hemen engellenmeden döndürmesi gerekir.<br /><br /> Bu davranış, doğrudan veya dolaylı olarak çağrıldığında kalıcı bir iletişim kutusu başlatma denetimleri için özellikle önemlidir. Kalıcı iletişim kapatılana kadar olay instigated herhangi bir UI Otomasyonu istemci engellenen kalır.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkin değilse.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu Kullanarak Denetim Çağırma](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
