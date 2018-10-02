---
title: UI Otomasyon Çağırma Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: f6afb850b16493bab79dd368ba1ff126305f96aa
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033525"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>UI Otomasyon Çağırma Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IInvokeProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.InvokePattern> Denetim düzeni etkinleştirildiğinde durumunu ancak bunun yerine başlatma korumak veya tek, belirli bir eylemi gerçekleştirmek denetimleri desteklemek için kullanılır. Durumunu, onay kutuları ve radyo düğmeleri gibi korumak denetimleri yerine uygulanmalı <xref:System.Windows.Automation.Provider.IToggleProvider> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider> sırasıyla. Invoke denetim desenini uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Çağır denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Denetimleri uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider> aynı davranışı başka bir denetim düzeni sağlayıcısı aracılığıyla açık değilse. Örneğin, varsa <xref:System.Windows.Automation.InvokePattern.Invoke%2A> denetim üzerinde yöntemi, aynı eylemi gerçekleştirir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> yöntemi, denetimin uygulamaz <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Bir denetim çağırma genellikle tıklayarak veya çift tıklayın veya ENTER, önceden tanımlı klavye kısayolu ya da diğer bazı tuş birleşimi tuşuna basarak gerçekleştirilir.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> (bir yanıt kendi ilişkili eylemi taşıyan bir denetime) olarak etkinleştirilmiş denetim üzerinde oluşturulur. Mümkünse, Olay denetimi eylemi tamamlandı ve engellemeden döndürülen sonra oluşmalıdır. Aşağıdaki senaryolarda Invoke isteği karşılamada önce çağrılan olayı tetikleyen:  
  
    -   Bu mümkün ve pratik eylem tamamlanana kadar beklenecek değildir.  
  
    -   Eylem kullanıcı etkileşimini gerektirir.  
  
    -   Eylem zaman alır ve önemli bir süre için engellemek çağıran istemci neden olur.  
  
-   Aracılığıyla denetim çağırma önemli yan etkileri varsa, bu yan etkileri açılmamalıdır <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> özelliği. Örneğin, olsa bile <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> seçimi ile ilişkilendirilmemiş <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> başka bir denetim seçili hale neden olabilir.  
  
-   Vurgu (veya fare bekletme) etkileri genellikle değil oluşturan çağrılan olay. Ancak, üzerine gelindiğinde kullanılacak durumuna bağlı bir eylem (aksine, görsel efekt neden) gerçekleştirmek denetimlerin desteklemelidir <xref:System.Windows.Automation.InvokePattern> denetim düzeni.  
  
> [!NOTE]
>  Bu uygulama yalnızca bir fare ile ilgili yan etkisi sonucunda denetim çağrılabilir erişilebilirlik sorunu kabul edilir.  
  
-   Bir denetim çağırma öğeyi seçmekten farklıdır. Ancak, denetimin bağlı olarak, onu çağırır bir yan etkisi olarak seçili hale neden olabilir. Örneğin, çağırma bir [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] Belgelerim klasöründeki belge liste öğesi hem öğeyi seçer ve belge açılır.  
  
-   Bir öğe kaldırılmasını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] açtıktan hemen sonra çağrılan ağaç. Olay geri çağırma tarafından sağlanan öğeden bilgi isteniyor sonucunda başarısız olabilir. Önbelleğe alınan bilgileri önceden getirme önerilen çözüm olabilir.  
  
-   Birden çok denetim düzenleri denetimlerini uygulayabilir. Örneğin, dolgu rengi denetimde [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] araç hem de uygular <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.ExpandCollapsePattern> denetim desenleri. <xref:System.Windows.Automation.ExpandCollapsePattern> Menü kullanıma sunar ve <xref:System.Windows.Automation.InvokePattern> etkin seçimin seçilen renk ile doldurur.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Gerekli üyeleri IInvokeProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|yöntemi|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> zaman uyumsuz bir çağrı ve hemen engellemeden döndürmesi gerekir.<br /><br /> Bu davranış, doğrudan veya dolaylı olarak çağrıldığında kalıcı bir iletişim kutusu başlatma denetimleri için özellikle önemlidir. Kalıcı iletişim kapatılana kadar olay instigated herhangi bir UI Otomasyon istemcisi engellenmiş durumda kalır.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetimin etkin değilse.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu Kullanarak Denetim Çağırma](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
