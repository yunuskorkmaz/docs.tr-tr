---
title: UI Otomasyonuna Genel Bakış
description: Windows Presentation Foundation (WPF) destekleyen Windows işletim sistemleri için erişilebilirlik çerçevesi olan Microsoft UI Otomasyonu 'na genel bakış konusunu okuyun.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 84b176e53f16ba0676e933efe9ed679bf425abc0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163258"
---
# <a name="ui-automation-overview"></a>UI Otomasyonuna Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], Microsoft Windows için desteklenen tüm işletim sistemlerinde kullanılabilen yeni erişilebilirlik çerçevesidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Masaüstü üzerindeki birçok öğeye programlı erişim sağlar [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve ekran okuyucular gibi yardımcı teknoloji ürünlerinin, son kullanıcılar hakkında bilgi sağlamasına [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve ' ın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] standart giriş dışında bir şekilde nasıl yönetilebilmesini sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ayrıca otomatik test betiklerinin ile etkileşime geçmesini sağlar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]farklı **Çalıştır** komutu aracılığıyla farklı kullanıcılar tarafından başlatılan süreçler arasındaki iletişimi etkinleştirmez.  
  
 UI Otomasyonu istemci uygulamaları birden çok çerçeve üzerinde çalışabilecekleri güvenlerle yazılabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Çekirdek, çerçeveler üzerinde çeşitli parçalar içeren herhangi bir farklılık vardır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Örneğin, `Content` bir düğmenin özelliği, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] `Caption` Win32 DÜĞMESI özelliği ve `ALT` HTML görüntüsünün özelliği, görünümdeki tek bir özelliğe eşlenir <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
UI Otomasyonu, .NET Framework çalıştıran desteklenen Windows işletim sistemlerinde tam işlevsellik sağlar (.NET Core 3,0 ile başlayan [.NET Framework sistem gereksinimlerini](../get-started/system-requirements.md) veya .NET Core sürümlerini inceleyin.  
  
 UI Otomasyon sağlayıcıları, yerleşik bir köprü oluşturma hizmeti aracılığıyla Microsoft Etkin Erişilebilirlik istemci uygulamaları için bazı destek sunar.  
  
<a name="Providers_and_Clients"></a>
## <a name="providers-and-clients"></a>Sağlayıcılar ve Istemciler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aşağıdaki tabloda gösterildiği gibi dört ana bileşene sahiptir.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sağlayıcı API 'SI (UIAutomationProvider.dll ve UIAutomationTypes.dll)|UI Otomasyon sağlayıcıları, öğeler hakkında bilgi sağlayan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve programlı girişe yanıt veren nesneler tarafından uygulanan bir arabirim tanımları kümesi.|  
|İstemci API 'SI (UIAutomationClient.dll ve UIAutomationTypes.dll)|Yönetilen kod için UI Otomasyonu istemci uygulamalarının, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve denetimlerine giriş göndermek için ve hakkında bilgi almasını sağlayan türler kümesi.|  
|UiAutomationCore.dll|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Sağlayıcılar ve istemciler arasındaki iletişimi işleyen temel alınan kod (bazen çekirdek olarak adlandırılır).|  
|UIAutomationClientsideProviders.dll|Standart eski denetimler için UI Otomasyon sağlayıcıları kümesi. ( [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimleri için yerel destek vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .) Bu destek, istemci uygulamaları için otomatik olarak kullanılabilir.|  
  
 Yazılım geliştiricinin perspektifinden, kullanmanın iki yolu vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] : özel denetimler (sağlayıcı API 'sini kullanarak) için destek oluşturmak ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerle iletişim kurmak için çekirdeği kullanan uygulamalar oluşturmak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (istemci API 'sini kullanarak). Odağunuza bağlı olarak, belgenin farklı bölümlerine başvurmalısınız. Kavramlar hakkında daha fazla bilgi edinebilir ve aşağıdaki bölümlerde pratik nasıl yapılır bilgisi elde edebilirsiniz.  
  
|Section|İlgili konular|Hedef kitle|  
|-------------|--------------------|--------------|  
|[UI Otomasyonu temelleri](index.md) (Bu bölüm)|Kavramlara genel bakış.|Tüm.|  
|[Yönetilen Kod İçin UI Otomasyon Sağlayıcılar](ui-automation-providers-for-managed-code.md)|Sağlayıcı API 'sini kullanmanıza yardımcı olacak genel bakış ve nasıl yapılır konuları.|Geliştiricilere denetim.|  
|[Yönetilen Kod İçin UI Otomasyon İstemcileri](ui-automation-clients-for-managed-code.md)|İstemci API 'SI kullanmanıza yardımcı olacak genel bakış ve nasıl yapılır konuları.|İstemci uygulaması geliştiricileri.|  
|[UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns.md)|Denetim desenlerinin sağlayıcılar tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabildiği hakkında bilgiler.|Tüm.|  
|[UI Otomasyon Metin Düzeni](ui-automation-text-pattern.md)|Metin denetim düzeninin sağlayıcılar tarafından nasıl uygulanması gerektiği ve istemciler için hangi işlevlerin kullanılabildiği hakkında bilgiler.|Tüm.|  
|[UI Otomasyon Denetim Türleri](ui-automation-control-types.md)|Farklı denetim türleri tarafından desteklenen özellikler ve Denetim desenleri hakkında bilgiler.|Tüm.|  
  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanları, bunları Içeren dll 'ler ve bunları kullanan izleyiciler listelenmektedir.  
  
|Ad Alanı|Başvurulan DLL 'Ler|Hedef kitle|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|Uıautomationclientuiautomationtypes|UI Otomasyonu istemci geliştiricileri; <xref:System.Windows.Automation.AutomationElement>nesneleri bulmak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylara kaydolmak ve denetim desenleriyle çalışmak için kullanılır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.Provider>|Uıautomationprovideruıautomationtypes|Dışındaki çerçeveler için UI Otomasyon sağlayıcılarının geliştiricileri [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] .|  
|<xref:System.Windows.Automation.Text>|Uıautomationclientuiautomationtypes|Dışındaki çerçeveler için UI Otomasyon sağlayıcılarının geliştiricileri [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , TextModel denetim düzenini uygulamak için kullanılır.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|İçin UI Otomasyon sağlayıcılarının geliştiricileri [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] .|  
  
<a name="UI_Automation_Model"></a>
## <a name="ui-automation-model"></a>UI Otomasyon modeli  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]' nin her parçasını, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] istemci uygulamalarının bir olarak gösterir <xref:System.Windows.Automation.AutomationElement> . Öğeler, kök öğe olarak masaüstüne sahip bir ağaç yapısında bulunur. İstemciler ağacın Ham görünümünü denetim görünümü veya içerik görünümü olarak filtreleyebilir. Uygulamalar, özel görünümler de oluşturabilir.  
  
 <xref:System.Windows.Automation.AutomationElement>nesneler, temsil ettikleri öğelerin ortak özelliklerini açığa çıkarır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Bu özelliklerden biri, temel görünümünü ve işlevselliğini tek tanınabilir bir varlık olarak tanımlayan denetim türüdür: Örneğin, bir düğme veya onay kutusu.  
  
 Ayrıca, öğeler denetim türlerine özgü özellikler sağlayan denetim düzenlerini kullanıma sunar. Denetim desenleri, istemcilerin öğe hakkında daha fazla bilgi almasını ve giriş sağlamasını sağlayan yöntemleri de kullanıma sunar.  
  
> [!NOTE]
> Denetim türleri ve Denetim desenleri arasında bire bir yazışmalar vardır. Bir denetim deseni birden çok denetim türü tarafından desteklenebilir ve bir denetim, her biri davranışının farklı yönlerini sunan birden fazla denetim desenini destekleyebilir. Örneğin, bir Birleşik giriş kutusunda en az iki denetim deseni vardır: genişletme ve daraltma yeteneğini temsil eden bir diğeri ise seçim mekanizmasını temsil eder. Ayrıntılar için bkz. [UI Otomasyonu Denetim türleri](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ayrıca olaylar aracılığıyla istemci uygulamalarına bilgiler sağlar. WinEvents 'ten farklı olarak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olaylar bir yayın mekanizmasına bağlı değildir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]istemciler belirli olay bildirimlerini kaydeder ve belirli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim deseninin bilgilerini olay işleyicilerine geçirilmesini isteyebilir. Ayrıca, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay, onu oluşturan öğesine bir başvuru içerir. Sağlayıcılar, herhangi bir istemcinin dinleme yapıp yapmayacağı temelinde olayları seçmeli olarak yükselterek performansı iyileştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyon Güvenliğine Genel Bakış](ui-automation-security-overview.md)
