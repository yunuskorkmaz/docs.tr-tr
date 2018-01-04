---
title: "Düğme Denetim Türü İçin UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
caps.latest.revision: "34"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5f9f2cb6ad3eb86fe60566fa19ecd59903d2c1d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-button-control-type"></a>Düğme Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] düğme denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri, Denetim desenleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar.  
  
 Bir kullanıcı gibi bir eylemi gerçekleştirmek için etkileşimde bir nesne bir düğme vardır **Tamam** ve **iptal** bir iletişim kutusu düğmeleri. Düğme denetimi, kullanıcının tamamlamak istediği tek bir komut eşlendiğinden kullanıma sunmak için basit bir denetimdir.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim desenleri ve olayları düğme denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri geçerlidir tüm düğme denetimlerine olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , düğme denetimlerine ilgilidir ve her bir görünümde bulunabilir açıklayan ağacı. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Düğme<br /><br /> -İmage (0 veya daha fazla)<br />-Metin (0 veya daha fazla)|Düğme|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı düğmesi uygulamak denetimleri özellikle ilgili özellikleri türü (örneğin, düğmesi denetimleri) denetler. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|Notlarına bakın.|Düğme denetimi genellikle temsil ettiği eylemi klavyeden hızlı bir şekilde gerçekleştirmek bir son kullanıcı etkinleştirmek için bir kısayol tuşu desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Bir sınırlayıcı dikdörtgenini ise desteklenir. Yoksa her sınırlayıcı dikdörtgenini içinde tıklanabilir noktasıdır ve özelleştirilmiş isabet testleri, gerçekleştirme sonra geçersiz kılabilir ve tıklatılabilir noktası sağlar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Düğme|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlarına bakın.|Yardım metni, düğme etkinleştirme sonuç ne olacağını belirtebilirsiniz. Bu genellikle bir araç ipucu sunulan bilgiler aynı türde olur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düğme denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düğme denetimi her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Düğme denetimlerinin içeriklerini tarafından otomatik olarak etiketlenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"button"|Düğme denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Düğme denetimi etiketlemek için kullanılan metin adıdır. Görüntüyü bir düğme etiketlemek için kullanılan her düğmenin adı özelliği için diğer metni sağlanmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri tüm düğmesi denetimleri tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Notlarına bakın.|Tüm düğmeleri Çağır denetim düzeni veya değiştirme denetim düzenini desteklemelidir. Çağırma düğmesi kullanıcının isteği komutunun gerçekleştirdiğinde desteklenir. Bu komut, kesme, kopyalama, yapıştırma veya silme gibi tek bir işlem eşler.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Notlarına bakın.|Tüm düğmeleri Çağır denetim düzeni veya değiştirme denetim düzenini desteklemelidir. İki durumlu düğme en fazla üç durumlu bir dizi aracılığıyla geçiş sırasında durumunda desteklenir. Genelde bu bir açık/kapalı belirli özellikler için anahtar olarak görülür.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Notlarına bakın.|Bölünmüş düğme alt sitesi olarak bir düğme barındırıldığında, alt düğmesi Invoke yerine ExpandCollapse düzeni veya değiştirme düzenini destekler. ExpandCollapse düzeni açma veya kapatma menü veya button öğesi ile ilişkili diğer alt yapısı için kullanılabilir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm düğmesi denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Bağlıdır|Çağır denetim düzeni denetimini destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Bağlıdır|Denetim değiştirme denetim düzenini destekliyorsa, bu olay desteklemesi gerekir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.Button>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
