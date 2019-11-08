---
title: UI Otomasyonuna Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: d803bd053acd876b3a38cfc52eb29818219e9423
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739579"
---
# <a name="ui-automation-overview"></a>UI Otomasyonuna Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]destekleyen tüm işletim sistemlerinde bulunan Microsoft Windows için yeni erişilebilirlik çerçevesidir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], masaüstündeki en [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğelere programlı erişim sağlar ve ekran okuyucular gibi yardımcı teknoloji ürünlerinin son kullanıcılara [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] hakkında bilgi sağlamasına ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] standart dışında bir şekilde işlemesini sağlamaya olanak tanır girişinin. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ayrıca otomatik test betiklerinin [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]etkileşime geçmesini sağlar.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] farklı kullanıcılar tarafından başlatılan işler arasındaki iletişimi farklı **Çalıştır** komutuyla etkinleştirmez.  
  
 UI Otomasyonu istemci uygulamaları birden çok çerçeve üzerinde çalışabilecekleri güvenlerle yazılabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek, çerçeveler içindeki çeşitli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]parçalara ayıran her türlü farkı maskeler. Örneğin, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmesinin `Content` özelliği, bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmesinin `Caption` özelliği ve bir HTML görüntüsünün `ALT` özelliği <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>görünümünde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tek bir özelliğe eşlenir.  
  
UI Otomasyonu, .NET Framework çalıştıran desteklenen Windows işletim sistemlerinde tam işlevsellik sağlar (.NET Core 3,0 ile başlayan [.NET Framework sistem gereksinimlerini](../get-started/system-requirements.md) veya .NET Core sürümlerini inceleyin.  
  
 UI Otomasyon sağlayıcıları, yerleşik bir köprü oluşturma hizmeti aracılığıyla Microsoft Etkin Erişilebilirlik istemci uygulamaları için bazı destek sunar.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Sağlayıcılar ve Istemciler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aşağıdaki tabloda gösterildiği gibi dört ana bileşene sahiptir.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sağlayıcı API 'SI (UIAutomationProvider. dll ve UIAutomationTypes. dll)|UI Otomasyon sağlayıcıları tarafından uygulanan, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri hakkında bilgi sağlayan ve programlı girişe yanıt veren nesneleri içeren bir arabirim tanımları kümesi.|  
|İstemci API 'SI (UIAutomationClient. dll ve UIAutomationTypes. dll)|Kullanıcı Arabirimi Otomasyonu istemci uygulamalarının [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] hakkında bilgi almasını ve denetimlere giriş göndermesini sağlayan yönetilen kod türleri kümesi.|  
|UIAutomationCore. dll|Sağlayıcılar ve istemciler arasındaki iletişimi işleyen temel alınan kod (bazen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek olarak adlandırılır).|  
|UIAutomationClientSideProviders. dll|Standart eski denetimler için UI Otomasyon sağlayıcıları kümesi. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimlerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]için yerel desteği vardır.) Bu destek, istemci uygulamaları için otomatik olarak kullanılabilir.|  
  
 Yazılım geliştiricisi açısından, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]kullanmanın iki yolu vardır: özel denetimler (sağlayıcı API 'sini kullanarak) için destek oluşturmak ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleriyle iletişim kurmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdeğini kullanan uygulamalar oluşturmak (istemci API 'sini kullanarak). Odağunuza bağlı olarak, belgenin farklı bölümlerine başvurmalısınız. Kavramlar hakkında daha fazla bilgi edinebilir ve aşağıdaki bölümlerde pratik nasıl yapılır bilgisi elde edebilirsiniz.  
  
|Bölüm|İlgili konular|Hedef Kitle|  
|-------------|--------------------|--------------|  
|[UI Otomasyonu temelleri](index.md) (Bu bölüm)|Kavramlara genel bakış.|Tüm.|  
|[Yönetilen Kod İçin UI Otomasyonu Sağlayıcıları](ui-automation-providers-for-managed-code.md)|Sağlayıcı API 'sini kullanmanıza yardımcı olacak genel bakış ve nasıl yapılır konuları.|Geliştiricilere denetim.|  
|[Yönetilen Kod İçin UI Otomasyonu İstemcileri](ui-automation-clients-for-managed-code.md)|İstemci API 'SI kullanmanıza yardımcı olacak genel bakış ve nasıl yapılır konuları.|İstemci uygulaması geliştiricileri.|  
|[UI Otomasyonu Denetim Desenleri](ui-automation-control-patterns.md)|Denetim desenlerinin sağlayıcılar tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabildiği hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Metin Deseni](ui-automation-text-pattern.md)|Metin denetim düzeninin sağlayıcılar tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabildiği hakkında bilgiler.|Tüm.|  
|[UI Otomasyonu Denetim Türleri](ui-automation-control-types.md)|Farklı denetim türleri tarafından desteklenen özellikler ve Denetim desenleri hakkında bilgiler.|Tüm.|  
  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanları, bunları içeren dll 'Ler ve bunları kullanan izleyiciler listelenmektedir.  
  
|Ad Alanı|Başvurulan DLL 'Ler|Hedef Kitle|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|Uıautomationclientuiautomationtypes|UI Otomasyonu istemci geliştiricileri; <xref:System.Windows.Automation.AutomationElement> nesneleri bulmak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylara kaydolmak ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleriyle çalışmak için kullanılır.|  
|<xref:System.Windows.Automation.Provider>|Uıautomationprovideruıautomationtypes|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dışındaki çerçeveler için UI Otomasyon sağlayıcılarının geliştiricileri.|  
|<xref:System.Windows.Automation.Text>|Uıautomationclientuiautomationtypes|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dışındaki çerçeveler için UI Otomasyon sağlayıcılarının geliştiricileri TextModel denetim düzenini uygulamak için kullanılır.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]için UI Otomasyon sağlayıcılarının geliştiricileri.|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>UI Otomasyon modeli  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] her parçayı istemci uygulamalarına <xref:System.Windows.Automation.AutomationElement>olarak sunar. Öğeler, kök öğe olarak masaüstüne sahip bir ağaç yapısında bulunur. İstemciler ağacın Ham görünümünü denetim görünümü veya içerik görünümü olarak filtreleyebilir. Uygulamalar, özel görünümler de oluşturabilir.  
  
 <xref:System.Windows.Automation.AutomationElement> nesneler, temsil ettikleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin ortak özelliklerini kullanıma sunar. Bu özelliklerden biri, temel görünümünü ve işlevselliğini tek tanınabilir bir varlık olarak tanımlayan denetim türüdür: Örneğin, bir düğme veya onay kutusu.  
  
 Ayrıca, öğeler denetim türlerine özgü özellikler sağlayan denetim düzenlerini kullanıma sunar. Denetim desenleri, istemcilerin öğe hakkında daha fazla bilgi almasını ve giriş sağlamasını sağlayan yöntemleri de kullanıma sunar.  
  
> [!NOTE]
> Denetim türleri ve Denetim desenleri arasında bire bir yazışmalar vardır. Bir denetim deseni birden çok denetim türü tarafından desteklenebilir ve bir denetim, her biri davranışının farklı yönlerini sunan birden fazla denetim desenini destekleyebilir. Örneğin, bir Birleşik giriş kutusunda en az iki denetim deseni vardır: genişletme ve daraltma yeteneğini temsil eden bir diğeri ise seçim mekanizmasını temsil eder. Ayrıntılar için bkz. [UI Otomasyonu Denetim türleri](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ayrıca olaylar aracılığıyla istemci uygulamalarına bilgiler sağlar. WinEvents 'ten farklı olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar bir yayın mekanizmasına dayalıdır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemcileri belirli olay bildirimlerini kaydeder ve belirli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim deseninin bilgilerini olay işleyicilerine geçirilmesini isteyebilir. Ayrıca, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı, onu oluşturan öğeye bir başvuru içerir. Sağlayıcılar, herhangi bir istemcinin dinleme yapıp yapmayacağı temelinde olayları seçmeli olarak yükselterek performansı iyileştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyonu Güvenliğine Genel Bakış](ui-automation-security-overview.md)
