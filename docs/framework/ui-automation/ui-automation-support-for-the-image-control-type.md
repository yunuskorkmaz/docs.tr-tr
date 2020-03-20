---
title: Görüntü Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Image control type
- control types, Image
- Image control type
ms.assetid: 4e0eeefb-e09b-46d2-b83b-0a7e35543ab8
ms.openlocfilehash: b77174a573b027f44be6104cda3d9846d12924e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179721"
---
# <a name="ui-automation-support-for-the-image-control-type"></a>Görüntü Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Görüntü denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Simgeler, bilgi grafikleri ve grafikler olarak kullanılan görüntü denetimleri Görüntü denetim türünü destekler. Arka plan veya filigran görüntüleri olarak kullanılan denetimler Görüntü denetim türünü desteklemez.  
  
 Aşağıdaki bölümler, Görüntü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü için gerekli ağaç yapısını, özelliklerini, denetim desenlerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm görüntü denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, görüntü denetimleri ile ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Görüntü|Resim (Görüntünün bilgi içerip içermediğine `IsContentElement` bağlıdır (özelliğin değerine göre değişir))|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle Görüntü denetim türüyle ilgili özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Istemciler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Görüntü denetiminin tıklatılabilir noktası, görüntü denetiminin sınırlayıcı dikdörtgeni içinde bir nokta olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bilgi içeren tüm görüntü denetimleri için Ad özelliği açıklanmalıdır. Bu bilgilere programlı erişim, grafiğe eşdeğer bir metin eşdeğerinin sağlanmasını gerektirir. Görüntü denetimi tamamen dekoratifse, yalnızca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünde gösterilmesi gerekir ve bir ad olması gerekmez. Kullanıcı Arabirimi çerçeveleri, kendi çerçeveleri içinde ayarlanabilen görüntülerde bir ALT veya alternatif metin özelliğini desteklemelidir. Bu özellik daha sonra [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ad özelliğiyle eşlenecektir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetime bir başvuru göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Görüntü|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"görüntü"|Görüntü denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Notlara bakın.|Görüntü denetimi, son kullanıcıya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zaten maruz kalmamış anlamlı bilgiler içerdiğinde ağacın içerik görünümüne eklenmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Görüntü denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|HelpText özelliği, denetimin gerçek görsel görünümünü (örneğin, beyaz 'X' içeren kırmızı bir kare) veya görüntüyle ilişkili diğer araç ipucu bilgilerini açıklayan yerelleştirilmiş bir dize ortaya çıkarır.<br /><br /> Görüntü denetimi hakkında daha fazla bilgi iletmek için uzun bir açıklama gerektiğinde bu özellik desteklenmelidir. Örneğin, karmaşık bir grafik veya diyagram. Bu özellik HTML LongDesc etiketine ve Ölçeklenebilir Vektör Grafikleri (SVG) Desc etiketine eşler. Görüntü denetimleriyle çalışan geliştiriciler, görsel açıklamanın denetimde ayarlanabilmesi için bir özelliği desteklemelidir. Bu özellik, UI Automation VisualDescription özelliğine eşlenmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Notlara bakın.|Görüntü denetimi, ekrandaki belirli bir öğe yle ilgili durum bilgilerini temsil ederse, denetim öğenin içinde yer almalıdır. Görüntü bir öğenin içinde bulunduğunda, öğenin durum özelliğini desteklemesi ve durum değiştiğinde uygun bildirimleri yükseltmesi gerekir.<br /><br /> Bir görüntü bağımsız bir denetim ise ve durum iletiyorsa, bu özellik desteklenmelidir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm görüntü denetimleri tarafından desteklenmesi gereken denetim desenlerini listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Denetim Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|-sına bağ -lıdır|Denetim bir ızgara kapsayıcıiçindeyse görüntü denetimi Izgara Öğesi deseni destekler.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|-sına bağ -lıdır|Denetim üstbilgi denetimleri olan bir kapsayıcı içinde ise görüntü denetimi Tablo Öğesi deseni destekler.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Hiçbir zaman|Görüntü denetimi tıklanabilir bir görüntü içeriyorsa, denetim, Düğme denetim türü gibi Invoke deseni destekleyen bir denetim türünü desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Hiçbir zaman|Görüntü denetimleri Seçim Öğesi deseni desteklememelidir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm görüntü denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Image>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
