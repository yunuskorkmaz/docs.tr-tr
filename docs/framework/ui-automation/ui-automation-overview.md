---
title: UI Otomasyonuna Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 06cbc82f3636c4063b445a0ccbe871e0be1dd847
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134679"
---
# <a name="ui-automation-overview"></a>UI Otomasyonuna Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Yeni bir erişilebilirlik çerçevesi için [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]destekleyen tüm işletim sistemleri üzerinden [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Çoğu programlı erişim sağlayan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri masaüstünde, yardımcı teknoloji ürünlerinin gibi etkinleştirme ekran okuyucuları hakkında bilgi sağlamak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] son kullanıcılara ve işlemek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] gerçekleştirmenin dışında standart giriş. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Otomatik test betikleri ile etkileşim kurmak ayrıca sağlar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Farklı kullanıcılar tarafından başlatılan işlemler arasındaki iletişimi etkinleştirmez **Çalıştır** komutu.  
  
 UI Otomasyonu istemci uygulamalar üzerinde birden çok çerçeveyi çalışacaktır güvencesi yazılabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Çekirdek maskeleri farklılıklarını temelini oluşturan çeşitli parçaları çerçeveleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Örneğin, `Content` özelliği bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmesi `Caption` özelliği bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmesi ve `ALT` HTML görüntü özelliği tüm eşlendi tek bir özelliğe <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] görünümü.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tam işlevsellik sağlar [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], ve [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 UI Otomasyonu sağlayıcıları için bazı desteği sunan [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] yerleşik bağlantı hizmeti aracılığıyla, istemci uygulamaları.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Sağlayıcılar ve istemciler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Aşağıdaki tabloda gösterildiği gibi dört ana bileşen vardır.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sağlayıcı [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll ve UIAutomationTypes.dll)|UI Otomasyon sağlayıcıları tarafından uygulanan arabirim tanımlarının bir dizi ilgili bilgi sağlayan nesneleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri ve programlı girişine yanıt vermedi.|  
|İstemci API'si (UIAutomationClient.dll ve UIAutomationTypes.dll)|Bir dizi türleri hakkında bilgi edinmek için UI Otomasyonu istemci uygulamaları etkinleştiren yönetilen kod için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve denetimlerine giriş göndermek için.|  
|UiAutomationCore.dll|Arka plandaki kod (olarak da adlandırılır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek), sağlayıcıları ve istemciler arasındaki iletişimi gerçekleştirir.|  
|UIAutomationClientsideProviders.dll|Eski standart denetimler için UI Otomasyonu sağlayıcıları bir dizi. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetiminiz için yerel destek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Bu destek, istemci uygulamaları için otomatik olarak kullanılabilir.|  
  
 Yazılım geliştirici açısından bakıldığında, kullanmanın iki yolu vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: özel denetimler (' % s'sağlayıcısı API'si kullanarak) için destek oluşturmak için ve kullanan uygulamaları oluşturma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ile iletişim kurmak için çekirdek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (kullanarak öğeleri İstemci API'si). Odağınızı bağlı olarak, belgelerinin farklı bölümlerine başvurmanız gerekir. Kavramları hakkında daha fazla bilgi edinmek ve aşağıdaki bölümlerde pratik yapılır bilgi elde edebilirsiniz.  
  
|Bölüm|Konu|Hedef Kitle|  
|-------------|--------------------|--------------|  
|[UI Otomasyon Temelleri](../../../docs/framework/ui-automation/index.md) (Bu bölüm)|Kavramları genel bakış.|Tüm.|  
|[Yönetilen Kod İçin UI Otomasyonu Sağlayıcıları](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Genel bakışlar ve API sağlayıcısı kullanmanıza yardımcı olması için nasıl yapılır konuları.|Denetim geliştiriciler.|  
|[Yönetilen Kod İçin UI Otomasyonu İstemcileri](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Genel bakışlar ve istemci API'si kullanmanıza yardımcı olması için nasıl yapılır konuları.|İstemci uygulaması geliştiricileri.|  
|[UI Otomasyonu Denetim Desenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Denetim desenlerini sağlayıcıları tarafından nasıl uygulanması gerekir ve istemciler için kullanılabilir işlevler hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Metin Deseni](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Metin denetim düzeni sağlayıcıları tarafından nasıl uygulanması gerekir ve istemciler için kullanılabilir işlevler hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Denetim Türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Farklı denetim türleri tarafından desteklenen özellikler ve denetim desenleri hakkında bilgi.|Tüm.|  
  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanları, bunları ve bunları kullanan İzleyici içeren dll.  
  
|Ad Alanı|Dll|Hedef Kitle|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|UI Otomasyonu istemci geliştiriciler; bulmak için kullanılan <xref:System.Windows.Automation.AutomationElement> nesneleri kaydetmek için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları ve iş ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Geliştiriciler dışında çerçeveleri için UI Otomasyonu sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Geliştiriciler dışında çerçeveleri için UI Otomasyonu sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; TextPattern denetim desenini uygulamak için kullanılır.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Geliştiriciler için UI Otomasyonu sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>UI otomasyon modeli  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Her bir sunar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] istemci uygulamalar için bir <xref:System.Windows.Automation.AutomationElement>. Öğeler, kök öğe olarak masaüstü ile bir ağaç yapısı içinde yer alır. İstemciler, bir denetimi görüntüleme veya içerik görünümü ağacı işlenmemiş bir görünümünü filtreleyebilirsiniz. Uygulamalar özel görünümlerinizi de oluşturabilirsiniz.  
  
 <xref:System.Windows.Automation.AutomationElement> nesneleri ortaya ortak özelliklerini [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri temsil ederler. Bu özelliklerinden biri tanınan tek bir varlık olarak kendi temel Görünüm ve işlevselliği tanımlayan denetim türü: Örneğin, bir düğme veya onay kutusu.  
  
 Ayrıca, öğeleri bunların denetim türlerine özgü özellikleri sağlayan denetim düzenleri ortaya çıkarır. Denetim düzenleri, istemcilerin öğeyle ilgili daha fazla bilgi almak ve giriş sağlamak için yöntemleri de kullanıma sunar.  
  
> [!NOTE]
>  Denetim türlerini ve denetim düzenleri arasında bire bir ilişkisi yoktur. Bir denetim düzeni birden çok denetim türleri tarafından desteklenmiyor olabilir ve bir denetim her biri farklı yönlerini davranışını gösterir, birden çok denetim düzenleri destekleyebilir. Örneğin, en az iki denetim düzenleri bir birleşik giriş kutusu vardır: biri genişletme ve daraltma yeteneğini temsil eder ve diğeri de seçim mekanizmasını temsil eder. Ayrıntılar için bkz: [UI Otomasyon denetim türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar ile istemci uygulamaları için bilgi de sağlar. Farklı [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar üzerinde bir yayın mekanizması bağlı değil. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemcilerin belirli olay bildirimleri için kaydolun ve bu özel talep edebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim düzeni bilgileri olay işleyicilerini geçirilir. Ayrıca, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay ortaya çıkan öğeye bir başvuru içerir. Sağlayıcıları, olayları seçerek, tüm istemciler olup olmadığını dinleyen bağlı olarak yükselterek performansı geliştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Özelliklerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [UI Otomasyonu Olaylarına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [UI Otomasyonu Güvenliğine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
