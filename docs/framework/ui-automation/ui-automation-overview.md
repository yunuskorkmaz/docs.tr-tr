---
title: UI Otomasyonuna Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 6f938302967e1b519105769717d326e5042a7bce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179915"
---
# <a name="ui-automation-overview"></a>UI Otomasyonuna Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]destekleyen tüm işletim sistemlerinde kullanılabilen Microsoft Windows için yeni [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]erişilebilirlik çerçevesidir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ekran okuyucular gibi [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] yardımcı teknoloji ürünlerinin son kullanıcılar hakkında bilgi vermesini ve standart girdi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dışındaki araçları manipüle [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] etmesini sağlayarak masaüstündeki öğelerin çoğuna programlı erişim sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ayrıca otomatik test komut dosyaları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ile etkileşim sağlar.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]komut **olarak Çalıştır** aracılığıyla farklı kullanıcılar tarafından başlatılan işlemler arasında iletişimi etkinleştirmez.  
  
 UI Automation istemci uygulamaları, birden fazla çerçeve üzerinde çalışacakları güvencesiyle yazılabilir. Çekirdek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] maskeleri çeşitli parçaları altında yatan çerçevelerde herhangi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]bir farklılıkları . Örneğin, bir `Content` [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmenin özelliği, `Caption` Win32 düğmesinin özelliği `ALT` ve HTML görüntüsünün [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği, görünümde tek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>bir özelliğe eşlenir.  
  
Kullanıcı Birsonucu Otomasyonu,.NET Framework'ü çalıştıran desteklenen Windows işletim sistemlerinde tam işlevsellik sağlar (bkz. [.NET Framework sistem gereksinimleri](../get-started/system-requirements.md) veya .NET Core 3.0 ile başlayan sürümleri.  
  
 Kullanıcı Arabirimi Otomasyon sağlayıcıları, yerleşik bir köprüleme hizmeti aracılığıyla Microsoft Etkin Erişilebilirlik istemcisi uygulamaları için bazı destek sunar.  
  
<a name="Providers_and_Clients"></a>
## <a name="providers-and-clients"></a>Sağlayıcılar ve İstemciler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]aşağıdaki tabloda gösterildiği gibi dört ana bileşeni vardır.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sağlayıcı API (UIAutomationProvider.dll ve UIAutomationTypes.dll)|Kullanıcı Arabirimi Otomasyon sağlayıcıları tarafından uygulanan arabirim tanımları kümesi, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler hakkında bilgi sağlayan ve programlı girişe yanıt veren nesneler.|  
|İstemci API (UIAutomationClient.dll ve UIAutomationTypes.dll)|UI Automation istemci uygulamalarının denetimler hakkında bilgi edinmesini [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve denetimlere giriş göndermesini sağlayan yönetilen kod için bir dizi tür.|  
|UiAutomationCore.dll|Sağlayıcılar ve istemciler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arasındaki iletişimi işleyen temel kod (bazen çekirdek olarak adlandırılır).|  
|UIAutomationClientsideProviders.dll|Standart eski denetimler için bir dizi UI Otomasyon sağlayıcısı. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontroller için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yerel destek var.) Bu destek istemci uygulamaları için otomatik olarak kullanılabilir.|  
  
 Yazılım geliştiricisinin bakış açısından, kullanmanın [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]iki yolu vardır: özel denetimler için destek oluşturmak (sağlayıcı API'sini kullanarak) ve öğelerle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iletişim kurmak için çekirdeği kullanan uygulamalar oluşturmak (istemci API'sını kullanarak). Odak noktanıza bağlı olarak, belgelerin farklı bölümlerine başvurmalısınız. Aşağıdaki bölümlerde kavramlar hakkında daha fazla bilgi edinebilir ve pratik nasıl öğrenilir bilgisini edinebilirsiniz.  
  
|Section|Konu|Hedef kitle|  
|-------------|--------------------|--------------|  
|[UI Otomasyon Temelleri](index.md) (bu bölüm)|Kavramlara genel bakış.|Tüm.|  
|[Yönetilen Kod İçin UI Otomasyon Sağlayıcılar](ui-automation-providers-for-managed-code.md)|Sağlayıcı API'sini kullanmanıza yardımcı olacak genel bakışlar ve nasıl yapılan konular.|Kontrol geliştiricileri.|  
|[Yönetilen Kod İçin UI Otomasyon İstemcileri](ui-automation-clients-for-managed-code.md)|İstemci API'sini kullanmanıza yardımcı olacak genel bakışlar ve nasıl yapılan konular.|İstemci uygulama geliştiricileri.|  
|[UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns.md)|Denetim desenleri sağlayıcıları tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabilir olduğu hakkında bilgi.|Tüm.|  
|[UI Otomasyon Metin Düzeni](ui-automation-text-pattern.md)|Metin denetimi deseni sağlayıcıları tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabilmesi hakkında bilgi.|Tüm.|  
|[UI Otomasyon Denetim Türleri](ui-automation-control-types.md)|Farklı denetim türleri tarafından desteklenen özellikler ve denetim desenleri hakkında bilgi.|Tüm.|  
  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanları, bunları içeren DL'ler ve bunları kullanan hedef kitle listelendir.  
  
|Ad Alanı|Başvurulan DL'ler|Hedef kitle|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientuiAutomationTypes|UI Automation istemci geliştiricileri; nesneleri bulmak, <xref:System.Windows.Automation.AutomationElement> olaylara [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaydolmak ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri ile çalışmak için kullanılır.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUiAutomationTypes|Dışındaki çerçeveler için UI Automation [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]sağlayıcılarının geliştiricileri.|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientuiAutomationTypes|Diğer çerçeveler için UI Automation [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]sağlayıcılarının geliştiricileri; TextPattern denetim deseni uygulamak için kullanılır.|  
|<xref:System.Windows.Automation.Peers>|Presentationframework|UI Otomasyon sağlayıcılarının [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]geliştiricileri.|  
  
<a name="UI_Automation_Model"></a>
## <a name="ui-automation-model"></a>UI Otomasyon Modeli  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]istemci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uygulamalarına her parçasını bir <xref:System.Windows.Automation.AutomationElement>. Öğeler, kök öğesi olarak masaüstü ile bir ağaç yapısı nda bulunur. İstemciler, ağacın ham görünümünü denetim görünümü veya içerik görünümü olarak filtreleyebilir. Uygulamalar da özel görünümler oluşturabilirsiniz.  
  
 <xref:System.Windows.Automation.AutomationElement>nesneler, temsil ettikleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin ortak özelliklerini ortaya çıkarır. Bu özelliklerden biri, temel görünümünü ve işlevselliğini tek bir tanınabilir varlık olarak tanımlayan denetim türüdür: örneğin, bir düğme veya onay kutusu.  
  
 Ayrıca, öğeler denetim türlerine özgü özellikler sağlayan denetim desenleri ortaya çıkarır. Denetim desenleri, istemcilerin öğe hakkında daha fazla bilgi edinmesini ve girdi sağlamasını sağlayan yöntemleri de ortaya çıkarır.  
  
> [!NOTE]
> Denetim türleri ve denetim desenleri arasında bire bir yazışma yoktur. Denetim deseni birden çok denetim türü tarafından desteklenebilir ve denetim, her biri davranışının farklı yönlerini ortaya çıkaran birden çok denetim deseni destekleyebilir. Örneğin, açılan kutunun en az iki denetim deleci vardır: biri genişletme ve daraltma yeteneğini temsil eden, diğeri ise seçim mekanizmasını temsil eden. Ayrıntılar için [UI Otomasyon Kontrol Türleri'ne](ui-automation-control-types.md)bakın.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ayrıca istemci uygulamalarına olaylar aracılığıyla bilgi sağlar. WinEvents'in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aksine, olaylar bir yayın mekanizmasına dayanmaz. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]istemciler belirli olay bildirimleri için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaydolur ve belirli özelliklerin ve denetim deseni bilgilerinin olay işleyicilerine aktarılmasını isteyebilir. Buna ek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olarak, bir olay onu yükselten öğeye bir başvuru içerir. Sağlayıcılar, istemcilerin dinleyip dinlemediğine bağlı olarak etkinlikleri seçerek artırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyonu Güvenliğine Genel Bakış](ui-automation-security-overview.md)
