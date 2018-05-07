---
title: UI Otomasyonuna Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b4752bf8f5fb75115618f95c4dab8b1359a1eb5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-overview"></a>UI Otomasyonuna Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Yeni erişilebilirlik çerçevesi için [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], kullanılabilir tüm işletim sistemlerinde destekleyen [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çoğu için programlı erişim sağlayan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri yardımcı teknoloji ürünlerinin gibi etkinleştirme masaüstünde, ekran okuyucuların hakkında bilgi sağlamak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] son kullanıcılara ve işlemek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] göre gelir dışında standart giriş. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ayrıca otomatikleştirilmiş test komut ile etkileşim sağlar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Farklı kullanıcılar tarafından başlatılan işlemleri arasındaki iletişimi etkinleştirmez **Farklı Çalıştır** komutu.  
  
 UI Otomasyonu istemci uygulamaları, birden çok çerçeveyi üzerinde çalışır güvencesi ile yazılabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Çekirdek maskeleri farklılıklarını çeşitli parçaları temelini oluşturan çerçeveleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Örneğin, `Content` özelliği bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmesini `Caption` özelliği bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmesi ve `ALT` HTML görüntü özelliği tüm eşlendi tek bir özelliğe <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] görünümü.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tam işlevsellik sağlar [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], ve [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 UI Otomasyon sağlayıcıları bazı desteği sunar [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] yerleşik bir köprü oluşturma hizmeti aracılığıyla istemci uygulamaları.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Sağlayıcılar ile istemciler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Aşağıdaki tabloda gösterildiği gibi dört ana bileşen vardır.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sağlayıcı [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll ve UIAutomationTypes.dll)|UI Otomasyon sağlayıcıları tarafından uygulanan Arabirim tanımları kümesi nesneleri hakkında bilgi sağlayan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri ve programlı giriş için yanıtlayın.|  
|İstemci API (UIAutomationClient.dll ve UIAutomationTypes.dll)|Türleri hakkında bilgi edinmek UI otomasyon istemci uygulamaları sağlayan yönetilen kod için bir dizi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve denetimleri için giriş göndermek için.|  
|UIAutomationCore.dll|Arka plandaki kod (bazen adlı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek) sağlayıcıları ve istemciler arasındaki iletişimi gerçekleştiren.|  
|UIAutomationClientsideProviders.dll|Standart eski denetimler için UI Otomasyon sağlayıcılar kümesi. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimleriniz için yerel destek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Bu destek, istemci uygulamalar otomatik olarak kullanılabilir.|  
  
 Yazılım geliştirme açısından kullanmanın iki yolu vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: (sağlayıcı API'sini kullanarak), özel denetimler için destek oluşturmak için ve kullanan uygulamaları oluşturma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ile iletişim kurmak için çekirdek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (kullanarak öğeleri İstemci API). Odağınız bağlı olarak, farklı belgelere bölümlerine başvurmalıdır. Kavramları hakkında bilgi edinin ve aşağıdaki bölümlerdeki pratik nasıl yapılır bilgisi geçirmesine.  
  
|Bölüm|Konuyla ilgili|Hedef Kitle|  
|-------------|--------------------|--------------|  
|[UI Otomasyon Temelleri](../../../docs/framework/ui-automation/index.md) (Bu bölüm)|Kavramlar genel bakış.|Tüm.|  
|[Yönetilen Kod İçin UI Otomasyonu Sağlayıcıları](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Genel bakış ve API sağlayıcısı kullanmanıza yardımcı olması için nasıl yapılır konuları.|Denetim geliştiriciler.|  
|[Yönetilen Kod İçin UI Otomasyonu İstemcileri](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Genel bakış ve istemci API'si kullanmanıza yardımcı olması için nasıl yapılır konuları.|İstemci uygulama geliştiricileri.|  
|[UI Otomasyonu Denetim Desenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Denetim desenleri sağlayıcıları tarafından nasıl uygulanması ve hangi işlevleri istemciler için kullanılabilir hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Metin Deseni](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Metin denetim düzeni sağlayıcıları tarafından nasıl uygulanması ve hangi işlevleri istemciler için kullanılabilir hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Denetim Türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Farklı denetim türleri tarafından desteklenen özellikler ve denetim düzenleri hakkında bilgi sağlar.|Tüm.|  
  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanları, bunları ve bunları kullanan hedef kitle içeren DLL'leri.  
  
|Ad Alanı|Başvurulan DLL'leri|Hedef Kitle|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|UI Otomasyonu istemci geliştiriciler; bulmak için kullanılan <xref:System.Windows.Automation.AutomationElement> nesneleri kaydetmek için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar ve çalışmak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Geliştiriciler dışında çerçeveler için UI Otomasyon sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Geliştiriciler dışında çerçeveler için UI Otomasyon sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; TextPattern denetim düzeni uygulamak için kullanılan.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Geliştiriciler için UI Otomasyon sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>UI otomasyon modeli  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Her parçasının sunan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] istemci uygulamaları için bir <xref:System.Windows.Automation.AutomationElement>. Öğeler kök öğesi olarak masaüstü ile bir ağaç yapısı içinde yer alır. İstemciler, ağaç denetimi görünüm veya içerik bir görünüm olarak ham görünümünü filtreleyebilirsiniz. Uygulamalar özel görünümlerinizi de oluşturabilirsiniz.  
  
 <xref:System.Windows.Automation.AutomationElement> nesneleri kullanıma ortak özelliklerini [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri bunlar temsil eder. Bu özelliklerden birini temel görünümünü ve işlevselliğini tek tanınabilir bir varlık olarak tanımlayan denetim türü olan: Örneğin, bir düğme veya onay kutusu.  
  
 Buna ek olarak, öğeleri denetim türlerini özgü özellikleri sağlayan denetim düzenleri kullanıma sunar. Denetim desenleri istemcileri öğe hakkında daha fazla bilgi almak için ve giriş sağlamanıza olanak sağlayan yöntemler de ortaya çıkarır.  
  
> [!NOTE]
>  Denetim türleri ve denetim desenleri arasında bire bir ilişkisi yok. Denetim düzeni birden çok denetim türleri tarafından desteklenmiyor olabilir ve bir denetim her biri farklı yönlerini davranışını gösteren birden çok denetim düzenleri desteği. Örneğin, en az iki denetim düzenleri birleşik giriş kutusu vardır: biri genişletme ve daraltma yeteneğini temsil eder ve diğeri de seçimi mekanizmasını temsil eder. Ayrıntılar için bkz: [UI Otomasyon denetim türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar ile istemci uygulamaları için bilgiler de sağlar. Farklı [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar üzerinde bir yayın mekanizması bağlı değil. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemcileri belirli olay bildirimleri kaydı ve bu özel isteyebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim düzeni bilgileri kendi olay işleyicileri bayraklarıdır. Ayrıca, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay ortaya çıkan öğeye başvuru içeriyor. Sağlayıcıları, olayları seçerek, tüm istemciler dinleme bağlı olarak yükselterek performansını iyileştirebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Özelliklerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [UI Otomasyonu Olaylarına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [UI Otomasyonu Güvenliğine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
