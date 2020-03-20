---
title: UI Otomasyon Sağlayıcılara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1f780ffc37b0aff93a3358c1980d271fe10c1321
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179884"
---
# <a name="ui-automation-providers-overview"></a>UI Otomasyon Sağlayıcılara Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 UI Automation sağlayıcıları, denetimlerin UI Automation istemci uygulamalarıyla iletişim kurmasını sağlar. Genel olarak, bir sağlayıcı tarafından [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] temsil edilen her denetim veya diğer farklı öğe bir sağlayıcı tarafından temsil edilir. Sağlayıcı öğe hakkında bilgi ortaya çıkarır ve isteğe bağlı olarak istemci uygulaması denetim ile etkileşim sağlayan denetim desenleri uygular.  
  
 İstemci uygulamaları genellikle doğrudan sağlayıcılarla çalışmak zorunda değildir. Win32, Windows Forms veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] çerçeveleri kullanan uygulamalardaki standart denetimlerin çoğu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] otomatik olarak sisteme maruz kalır. Özel denetimleri uygulayan uygulamalar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da bu denetimler için sağlayıcılar uygulayabilir ve istemci uygulamaları onlara erişmek için herhangi bir özel adım atmak zorunda değildir.  
  
 Bu konu, özellikle Windows Forms [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve Win32 pencerelerinde yapılan denetimler için denetim geliştiricilerin sağlayıcıları nasıl uyguladığına genel bir bakış sağlar.  
  
<a name="Types_of_Providers"></a>
## <a name="types-of-providers"></a>Sağlayıcı Türleri  
 UI Otomasyon sağlayıcıları iki kategoriye ayrılır: istemci tarafı sağlayıcıları ve sunucu tarafı sağlayıcıları.  
  
### <a name="client-side-providers"></a>İstemci tarafı sağlayıcıları  
 İstemci tarafı sağlayıcıları, ui automation istemcileri tarafından desteklemeyen veya tam olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]desteklemeyen bir uygulamayla iletişim kurmak için uygulanır. İstemci tarafı sağlayıcıları genellikle Windows iletileri göndererek ve alarak işlem sınırı boyunca sunucuyla iletişim kurar.  
  
 Win32, Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulamalardaki denetimler için Kullanıcı Arabirimi Otomasyonu sağlayıcıları işletim sisteminin bir parçası olarak sağlandığı için, istemci uygulamalarının nadiren kendi sağlayıcılarını uygulaması gerekir ve bu genel bakış bunları daha fazla kapsamaz.  
  
### <a name="server-side-providers"></a>Sunucu tarafı sağlayıcıları  
 Sunucu tarafı sağlayıcıları özel denetimler veya Win32, Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Sunucu tarafı sağlayıcıları, istemcilerin isteklerine hizmet eden [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek sisteme arabirimleri maruz bırakarak işlem sınırı boyunca istemci uygulamalarıyla iletişim kurar.  
  
<a name="AutomationProviderConcepts"></a>
## <a name="ui-automation-provider-concepts"></a>UI Otomasyon Sağlayıcı Kavramları  
 Bu bölümde, Kullanıcı Arabirimi Otomasyonu sağlayıcılarının uygulanması için anlamanız gereken bazı temel kavramlar hakkında kısa açıklamalar yer almaktadır.  
  
### <a name="elements"></a>Öğeler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeleri, UI Automation istemcileri tarafından [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] görülebilen parçalardır. Örnekler uygulama pencereleri, bölmeleri, düğmeleri, araç ipuçlarını, liste kutuları ve liste öğeleriiçerir.  
  
### <a name="navigation"></a>Gezinti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elemanlar istemcilere [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç olarak maruz kalır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bir öğeden diğerine gezinerek ağacı inşa eder. Gezinti, her biri bir üst öğeyi, kardeşleri ve alt öğeyi işaret eden her öğe için sağlayıcılar tarafından etkinleştirilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın istemci görünümü hakkında daha fazla bilgi için, [Kullanıcı Arabirimi Otomasyon Uaä](ui-automation-tree-overview.md)ına Genel Bakış' a bakın.  
  
### <a name="views"></a>Görünümler  
 İstemci, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aşağıdaki tabloda gösterildiği gibi ağacı üç temel görünümde görebilir.  
  
|||  
|-|-|  
|Ham görünüm|Tüm öğeleri içerir.|  
|Denetim görünümü|Denetimler olan öğeleri içerir.|  
|İçerik görünümü|İçeriği olan öğeler içerir.|  
  
 Ağacın istemci görünümleri hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi için [UI Automation Tree Genel Bakış](ui-automation-tree-overview.md)bölümüne bakın.  
  
 Bir öğeyi içerik öğesi veya denetim öğesi olarak tanımlamak sağlayıcı nın uygulamasının sorumluluğundadır. Denetim öğeleri içerik öğeleri olabilir veya olmayabilir, ancak tüm içerik öğeleri denetim öğeleridir.  
  
### <a name="frameworks"></a>Framework’ler  
 Çerçeve, alt denetimleri, isabet testi ve ekranın bir alanında işleme yöneten bir bileşendir. Örneğin, genellikle HWND olarak adlandırılan Win32 penceresi, menü çubuğu, durum [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çubuğu ve düğmeler gibi birden çok öğe içeren bir çerçeve olarak hizmet verebilir.  
  
 Liste kutuları ve ağaç görünümleri gibi Win32 kapsayıcı denetimleri, alt öğeleri işlemek ve üzerlerinde isabet testi gerçekleştirmek için kendi kodlarını içerdikleri için çerçeve olarak kabul edilir. Bunun aksine, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] işleme ve isabet testi içeren [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pencere tarafından işleniyor, çünkü bir liste kutusu bir çerçeve değildir.  
  
 Bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uygulamada farklı çerçeveler yapılabilir. Örneğin, bir HWND uygulama penceresi, bir HWND'deki açılan kutu gibi bir bileşen içeren Dinamik HTML (DHTML) içerebilir.  
  
### <a name="fragments"></a>Fragments  
 Parça, belirli bir çerçevedeki öğelerin tam bir alt ağacıdır. Alt ağacın kök düğümündeki öğeye parça kökü denir. Bir parça kök bir üst öğeye sahip değildir, ancak genellikle win32 penceresi (HWND) gibi başka bir çerçeve içinde barındırılır.  
  
### <a name="hosts"></a>Ana bilgisayarlar  
 Her parçanın kök düğümü, genellikle win32 penceresinde (HWND) bir öğede barındırılmalıdır. Bunun istisnası, başka bir öğede barındırılan olmayan masaüstüdür. Özel denetimin ana bilgisayarı, uygulama penceresi veya üst düzey denetim grupları içerebilecek başka bir pencere değil, denetimin kendisinin HWND'sidir.  
  
 Bir parçanın ev sahibi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmet sağlamada önemli bir rol oynar. Parça kökünde gezinmeyi sağlar ve özel sağlayıcının bunları uygulamak zorunda kalmaması için bazı varsayılan özellikler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
