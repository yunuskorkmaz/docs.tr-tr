---
title: UI Otomasyon Sağlayıcılara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1ffb8101ba0182c8ff11667f59d9bc10c5ffe670
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629565"
---
# <a name="ui-automation-providers-overview"></a>UI Otomasyon Sağlayıcılara Genel Bakış
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 UI Otomasyon sağlayıcıları, kullanıcıların UI Otomasyonu istemci uygulamalarıyla iletişim kurmasını sağlar. Genel olarak, içindeki [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] her denetim veya diğer ayrı öğe bir sağlayıcı tarafından temsil edilir. Sağlayıcı, öğesi hakkında bilgi gösterir ve isteğe bağlı olarak, istemci uygulamanın denetimle etkileşime geçmesini sağlayan denetim düzenlerini uygular.  
  
 İstemci uygulamalarının genellikle doğrudan sağlayıcılarıyla çalışması gerekmez. [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , Veya çerçevelerini[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] kullanan uygulamalardaki Standart denetimlerin çoğu otomatik olarak sisteme sunulur. [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] Özel denetimleri uygulayan uygulamalar da bu denetimler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları uygulayabilir ve istemci uygulamalarının bunlara erişim kazanmak için özel adımlar yapması gerekmez.  
  
 Bu konu, denetim geliştiricilerinin sağlayıcıları nasıl uygulayacağından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili bir genel bakış sunar ve özellikle ve [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] Windows içindeki [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] denetimler için.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Sağlayıcı türleri  
 UI Otomasyonu sağlayıcıları iki kategoriye ayrılır: istemci tarafı sağlayıcılar ve sunucu tarafı sağlayıcılar.  
  
### <a name="client-side-providers"></a>İstemci tarafı sağlayıcıları  
 İstemci tarafı sağlayıcılar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Kullanıcı Arabirimi Otomasyonu istemcileri tarafından desteklenmeyen veya tam olarak desteklenmeyen bir uygulamayla iletişim kuracak şekilde uygulanır. İstemci tarafı sağlayıcılar, genellikle Windows iletileri gönderip alarak işlem sınırının tamamında sunucusuyla iletişim kurar.  
  
 , Windows Forms veya [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulamalar içindeki denetimler için UI Otomasyonu sağlayıcıları işletim sisteminin bir parçası olarak sağlandığı için, istemci uygulamalarının nadiren kendi sağlayıcılarını uygulaması gerekir ve bu genel bakış bunları kapsamaz μ.  
  
### <a name="server-side-providers"></a>Sunucu tarafı sağlayıcıları  
 Sunucu tarafı sağlayıcılar [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], özel denetimler veya Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dışındaki bir UI çerçevesini temel alan uygulamalar tarafından uygulanır.  
  
 Sunucu tarafı sağlayıcılar, istemcileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek sisteme sunarak işlem sınırında istemci uygulamalarıyla iletişim kurar, bu da istemcilerden gelen istekleri üstlenir.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>UI Otomasyon sağlayıcısı kavramları  
 Bu bölüm, UI Otomasyon sağlayıcılarını uygulamak için anlamanız gereken bazı temel kavramların kısa açıklamalarını sunmaktadır.  
  
### <a name="elements"></a>Öğeler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeler, UI Otomasyonu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] istemcilerinin görebileceği parçalarından oluşur. Örnek olarak uygulama pencereleri, bölmeler, düğmeler, araç ipuçları, liste kutuları ve liste öğeleri bulunur.  
  
### <a name="navigation"></a>Gezinti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeler, istemcilere [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç olarak gösterilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bir öğeden diğerine giderek ağacı oluşturur. Gezinti, her biri bir üst, eşdüzey öğe ve alt öğeye işaret eden her öğe için sağlayıcılar tarafından etkinleştirilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın istemci görünümü hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Görünümler  
 Bir istemci, aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gösterildiği gibi, ağacı üç ana görünümde görüntüleyebilir.  
  
|||  
|-|-|  
|Ham görünüm|Tüm öğeleri içerir.|  
|Denetim görünümü|Denetimler olan öğeleri içerir.|  
|İçerik görünümü|İçeriği olan öğeleri içerir.|  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın istemci görünümleri hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Bu, bir öğeyi içerik öğesi veya denetim öğesi olarak tanımlamak için sağlayıcı uygulamasının sorumluluğundadır. Denetim öğeleri de içerik öğeleri olabilir veya olmayabilir, ancak tüm içerik öğeleri denetim öğeleridir.  
  
### <a name="frameworks"></a>Çerçeveler  
 Çerçeve, ekranın bir alanında alt denetimleri, isabet sınamasını ve işlemeyi yöneten bir bileşendir. Örneğin, genellikle HWND [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] olarak anılan bir pencere, bir menü çubuğu, bir durum çubuğu ve düğmeler gibi birden çok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe içeren bir çerçeve işlevi görebilir.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]liste kutuları ve ağaç görünümleri gibi kapsayıcı denetimleri, alt öğeleri işlemek ve bunlar üzerinde isabet testi gerçekleştirmek için kendi kodlarını içerdiğinden çerçeveler olarak değerlendirilir. Bunun aksine, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] liste kutusu çerçeve değildir, çünkü işleme ve isabet testi içeren [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pencere tarafından işlenir.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Uygulamasında bir uygulama farklı çerçevelerden oluşabilir. Örneğin, bir HWND uygulama penceresi, bir HWND içindeki Birleşik giriş kutusu gibi bir bileşeni içeren dinamik HTML (DHTML) içerebilir.  
  
### <a name="fragments"></a>Parçalar  
 Bir parça, belirli bir çerçeveden öğelerin tüm alt ağaclarından oluşur. Alt ağacın kök düğümündeki öğesine bir parça kökü denir. Parça kökünün bir üst öğesi yoktur, ancak genellikle bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] pencere (hwnd) içinde bir diğer çerçevede barındırılır.  
  
### <a name="hosts"></a>Bilgisayarlarınızı  
 Her parçanın kök düğümü, genellikle bir [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] pencere (hwnd) öğesinde barındırılmalıdır. Özel durum, başka bir öğede barındırılmayan masaüsttür. Özel bir denetimin Konağı, uygulama penceresi veya üst düzey denetim grupları içerebilen herhangi bir pencere değil, denetimin kendisidir.  
  
 Bir parçanın ana bilgisayarı, hizmetleri sağlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için önemli bir rol oynar. Parça köküne gezinmeyi sağlar ve özel sağlayıcının bunları uygulamak zorunda kalmaması için bazı varsayılan özellikleri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
