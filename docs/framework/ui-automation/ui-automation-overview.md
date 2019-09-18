---
title: UI Otomasyonuna Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 4a88cf077c061746f9bc9f4aa0122d2f09b6fbd7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042272"
---
# <a name="ui-automation-overview"></a>UI Otomasyonuna Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)][!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], tarafından desteklenen [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]tüm işletim sistemlerinde kullanılabilen yeni erişilebilirlik çerçevesidir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Masaüstü üzerindeki birçok [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeye programlı erişim sağlar ve ekran okuyucular gibi yardımcı teknoloji ürünlerinin, son [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcılar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] hakkında bilgi sağlamasına ve tarafından şu şekilde değişiklik yapmasına olanak tanır Standart giriş. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ayrıca otomatik test betiklerinin ile [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]etkileşime geçmesini sağlar.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]farklı **Çalıştır** komutu aracılığıyla farklı kullanıcılar tarafından başlatılan süreçler arasındaki iletişimi etkinleştirmez.  
  
 UI Otomasyonu istemci uygulamaları birden çok çerçeve üzerinde çalışabilecekleri güvenlerle yazılabilir. Çekirdek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , çerçeveler üzerinde çeşitli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]parçalar içeren herhangi bir farklılık vardır. Örneğin `Content` , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmenin özelliği, `Caption` bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmenin özelliği ve `ALT` HTML görüntüsünün özelliği, görünümdeki tek bir özelliğe <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>eşlenir.  
  
UI Otomasyonu, .NET Framework çalıştıran desteklenen Windows işletim sistemlerinde tam işlevsellik sağlar (.NET Core 3,0 ile başlayan [.NET Framework sistem gereksinimlerini](../get-started/system-requirements.md) veya .NET Core sürümlerini inceleyin.  
  
 UI Otomasyon sağlayıcıları, yerleşik bir köprü oluşturma hizmeti aracılığıyla Microsoft Etkin Erişilebilirlik istemci uygulamaları için bazı destek sunar.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Sağlayıcılar ve Istemciler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aşağıdaki tabloda gösterildiği gibi dört ana bileşene sahiptir.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sağlayıcı API 'SI (UIAutomationProvider. dll ve UIAutomationTypes. dll)|UI Otomasyon sağlayıcıları, öğeler hakkında [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bilgi sağlayan ve programlı girişe yanıt veren nesneler tarafından uygulanan bir arabirim tanımları kümesi.|  
|İstemci API 'SI (UIAutomationClient. dll ve UIAutomationTypes. dll)|Yönetilen kod için UI Otomasyonu istemci uygulamalarının, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve denetimlerine giriş göndermek için ve hakkında bilgi almasını sağlayan türler kümesi.|  
|UIAutomationCore. dll|Sağlayıcılar ve istemciler arasındaki iletişimi işleyen temel [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] alınan kod (bazen çekirdek olarak adlandırılır).|  
|UIAutomationClientSideProviders. dll|Standart eski denetimler için UI Otomasyon sağlayıcıları kümesi. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimleri için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yerel destek vardır.) Bu destek, istemci uygulamaları için otomatik olarak kullanılabilir.|  
  
 Yazılım geliştiricinin perspektifinden, kullanmanın [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]iki yolu vardır: özel denetimler (sağlayıcı API 'sini kullanarak) için destek oluşturmak ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerle iletişim kurmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdeği kullanan uygulamalar oluşturmak (kullanarak istemci API 'SI). Odağunuza bağlı olarak, belgenin farklı bölümlerine başvurmalısınız. Kavramlar hakkında daha fazla bilgi edinebilir ve aşağıdaki bölümlerde pratik nasıl yapılır bilgisi elde edebilirsiniz.  
  
|Bölüm|İlgili konular|Hedef Kitle|  
|-------------|--------------------|--------------|  
|[UI Otomasyonu temelleri](index.md) (Bu bölüm)|Kavramlara genel bakış.|Tüm.|  
|[Yönetilen Kod İçin UI Otomasyonu Sağlayıcıları](ui-automation-providers-for-managed-code.md)|Sağlayıcı API 'sini kullanmanıza yardımcı olacak genel bakış ve nasıl yapılır konuları.|Geliştiricilere denetim.|  
|[Yönetilen Kod İçin UI Otomasyonu İstemcileri](ui-automation-clients-for-managed-code.md)|İstemci API 'SI kullanmanıza yardımcı olacak genel bakış ve nasıl yapılır konuları.|İstemci uygulaması geliştiricileri.|  
|[UI Otomasyonu Denetim Desenleri](ui-automation-control-patterns.md)|Denetim desenlerinin sağlayıcılar tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabildiği hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Metin Deseni](ui-automation-text-pattern.md)|Metin denetim düzeninin sağlayıcılar tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabildiği hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Denetim Türleri](ui-automation-control-types.md)|Farklı denetim türleri tarafından desteklenen özellikler ve Denetim desenleri hakkında bilgiler.|Tüm.|  
  
 Aşağıdaki tabloda ad alanları [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bunları içeren dll 'ler ve bunları kullanan izleyiciler listelenmektedir.  
  
|Ad Alanı|Başvurulan DLL 'Ler|Hedef Kitle|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|Uıautomationclientuiautomationtypes|UI Otomasyonu istemci geliştiricileri; nesneleri bulmak <xref:System.Windows.Automation.AutomationElement> , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylara kaydolmak ve denetim desenleriyle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çalışmak için kullanılır.|  
|<xref:System.Windows.Automation.Provider>|Uıautomationprovideruıautomationtypes|Dışındaki [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çerçeveler için UI Otomasyon sağlayıcılarının geliştiricileri.|  
|<xref:System.Windows.Automation.Text>|Uıautomationclientuiautomationtypes|Dışındaki [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çerçeveler için UI Otomasyon sağlayıcılarının geliştiricileri, TextModel denetim düzenini uygulamak için kullanılır.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|İçin [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]UI Otomasyon sağlayıcılarının geliştiricileri.|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>UI Otomasyon modeli  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]' nin her parçasını, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] istemci uygulamalarının bir <xref:System.Windows.Automation.AutomationElement>olarak gösterir. Öğeler, kök öğe olarak masaüstüne sahip bir ağaç yapısında bulunur. İstemciler ağacın Ham görünümünü denetim görünümü veya içerik görünümü olarak filtreleyebilir. Uygulamalar, özel görünümler de oluşturabilir.  
  
 <xref:System.Windows.Automation.AutomationElement>nesneler, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] temsil ettikleri öğelerin ortak özelliklerini açığa çıkarır. Bu özelliklerden biri, temel görünümünü ve işlevselliğini tek tanınabilir bir varlık olarak tanımlayan denetim türüdür: Örneğin, bir düğme veya onay kutusu.  
  
 Ayrıca, öğeler denetim türlerine özgü özellikler sağlayan denetim düzenlerini kullanıma sunar. Denetim desenleri, istemcilerin öğe hakkında daha fazla bilgi almasını ve giriş sağlamasını sağlayan yöntemleri de kullanıma sunar.  
  
> [!NOTE]
> Denetim türleri ve Denetim desenleri arasında bire bir yazışmalar vardır. Bir denetim deseni birden çok denetim türü tarafından desteklenebilir ve bir denetim, her biri davranışının farklı yönlerini sunan birden fazla denetim desenini destekleyebilir. Örneğin, bir Birleşik giriş kutusunda en az iki denetim deseni vardır: genişletme ve daraltma yeteneğini temsil eden bir diğeri ise seçim mekanizmasını temsil eder. Ayrıntılar için bkz. [UI Otomasyonu Denetim türleri](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ayrıca olaylar aracılığıyla istemci uygulamalarına bilgiler sağlar. Aksine [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)] ,[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar bir yayın mekanizmasına bağlı değildir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]istemciler belirli olay bildirimlerini kaydeder ve belirli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim deseninin bilgilerini olay işleyicilerine geçirilmesini isteyebilir. Ayrıca, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay, onu oluşturan öğesine bir başvuru içerir. Sağlayıcılar, herhangi bir istemcinin dinleme yapıp yapmayacağı temelinde olayları seçmeli olarak yükselterek performansı iyileştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyonu Güvenliğine Genel Bakış](ui-automation-security-overview.md)
