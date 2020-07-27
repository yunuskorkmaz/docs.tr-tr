---
title: Görüntü Denetim Türü İçin UI Otomasyon Desteği
description: Görüntü denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Image control type
- control types, Image
- Image control type
ms.assetid: 4e0eeefb-e09b-46d2-b83b-0a7e35543ab8
ms.openlocfilehash: 97a71b31609566ca081dee1c66b911f0ad534a50
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166946"
---
# <a name="ui-automation-support-for-the-image-control-type"></a>Görüntü Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , görüntü denetim türü için destek hakkında bilgi sağlar. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Simgeler, bilgilendirici grafikler ve grafikler olarak kullanılan görüntü denetimleri, görüntü denetim türünü destekleyecektir. Arka plan veya filigran görüntüleri olarak kullanılan denetimler görüntü denetim türünü desteklemez.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] görüntü denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm görüntü denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, görüntü denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Görüntü|Görüntü (görüntünün bilgileri içerip içermediğini belirtir (özelliğin değerine göre `IsContentElement` ))|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle görüntü denetim türüyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Görüntü denetiminin tıklatılabilir noktası, görüntü denetiminin sınırlayıcı dikdörtgeninin içindeki bir nokta olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Ad özelliği, bilgi içeren tüm görüntü denetimleri için sunulmalıdır. Bu bilgilere programlı erişim, grafiğe metin eşdeğerini sağlanması gerekir. Görüntü denetimi tamamen dekoratif ise, yalnızca ağacın denetim görünümünde gösterilmesi gerekir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve bir ada sahip olması gerekmez. UI çerçeveleri, çerçevelerinden ayarlanabilir olan görüntülerde ALT veya alternatif metin özelliğini desteklemelidir. Bu özellik daha sonra [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Name özelliğine eşlenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Görüntü|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|görüntüyle|Görüntü denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Notlara bakın.|Görüntü denetimi, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] son kullanıcıya önceden gösterilmeyen anlamlı bilgiler içerdiğinde ağacın içerik görünümüne dahil olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Görüntü denetimi her zaman ağacın denetim görünümüne dahil edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|HelpText özelliği, denetimin gerçek görsel görünümünü (örneğin, beyaz ' X ' içeren kırmızı bir kare) veya görüntüyle ilişkili diğer araç ipucu bilgilerini açıklayan yerelleştirilmiş bir dize gösterir.<br /><br /> Görüntü denetimi hakkında daha fazla bilgi iletmek için uzun bir açıklama gerektiğinde bu özellik desteklenmelidir. Örneğin, karmaşık bir grafik veya diyagram. Bu özellik HTML LongDesc etiketine ve ölçeklenebilir vektör grafikleri (SVG) desc etiketine eşlenir. Görüntü denetimleriyle çalışan geliştiricilerin, denetimde görsel açıklamanın ayarlanmasıyla izin vermek için bir özelliği desteklemesi gerekir. Bu özellik UI Automation VisualDescription özelliği ile eşlenmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Notlara bakın.|Görüntü denetimi ekrandaki belirli bir öğeyle ilgili durum bilgilerini temsil ediyorsa, denetimin öğe içinde yer almalıdır. Görüntü bir öğe içinde bulunduğunda, öğe Status özelliğini desteklemelidir ve durum değiştiğinde uygun bildirimleri yükseltir.<br /><br /> Bir görüntü tek başına denetimdir ve durumu alıyorsa, bu özelliğin desteklenmesi gerekir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm görüntü denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Şekline|Denetim bir kılavuz kapsayıcısı içindeyse, görüntü denetimi kılavuz öğe modelini destekler.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Şekline|Denetim, üst bilgi denetimlerine sahip bir kapsayıcıda yer alıyorsa, görüntü denetimi tablo öğesi modelini destekler.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Asla|Görüntü denetimi tıklatılabilir bir görüntü içeriyorsa denetim, düğme denetim türü gibi Invoke deseninin desteklendiği bir denetim türünü desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Asla|Görüntü denetimleri seçim öğesi modelini desteklememelidir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm görüntü denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Asla|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Asla|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Asla|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Asla|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Image>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
