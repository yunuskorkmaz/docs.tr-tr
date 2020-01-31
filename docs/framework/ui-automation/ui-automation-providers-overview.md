---
title: UI Otomasyon Sağlayıcılara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 98208f1e1fa1b540bf3880e33478854128505233
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778780"
---
# <a name="ui-automation-providers-overview"></a>UI Otomasyon Sağlayıcılara Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 UI Otomasyon sağlayıcıları, kullanıcıların UI Otomasyonu istemci uygulamalarıyla iletişim kurmasını sağlar. Genel olarak, bir [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] her denetim veya diğer ayrı öğe bir sağlayıcı tarafından temsil edilir. Sağlayıcı, öğesi hakkında bilgi gösterir ve isteğe bağlı olarak, istemci uygulamanın denetimle etkileşime geçmesini sağlayan denetim düzenlerini uygular.  
  
 İstemci uygulamalarının genellikle doğrudan sağlayıcılarıyla çalışması gerekmez. Win32, Windows Forms veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] çerçeveleri kullanan uygulamalardaki Standart denetimlerin çoğu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistemine otomatik olarak sunulur. Özel denetimleri uygulayan uygulamalar da bu denetimler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları uygulayabilir ve istemci uygulamalarının bunlara erişim kazanmak için özel adımlar yapması gerekmez.  
  
 Bu konu, denetim geliştiricilerinin, özellikle Windows Forms ve Win32 Windows denetimlerinde bulunan denetimler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları nasıl uygulayacağından ilgili bir genel bakış sunar.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Sağlayıcı türleri  
 UI Otomasyonu sağlayıcıları iki kategoriye ayrılır: istemci tarafı sağlayıcılar ve sunucu tarafı sağlayıcılar.  
  
### <a name="client-side-providers"></a>İstemci tarafı sağlayıcıları  
 İstemci tarafı sağlayıcılar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından desteklenmeyen veya tam olarak desteklenmeyen bir uygulamayla iletişim kurmak için UI Otomasyon istemcileri tarafından uygulanır. İstemci tarafı sağlayıcılar, genellikle Windows iletileri gönderip alarak işlem sınırının tamamında sunucusuyla iletişim kurar.  
  
 Win32, Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulamaları için UI Otomasyon sağlayıcıları işletim sisteminin bir parçası olarak sağlandığı için, istemci uygulamalarının nadiren kendi sağlayıcılarını uygulaması gerekir ve bu genel bakış bunları daha fazla kapsamaz.  
  
### <a name="server-side-providers"></a>Sunucu tarafı sağlayıcıları  
 Sunucu tarafı sağlayıcılar, özel denetimler veya Win32, Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dışında bir UI çerçevesini temel alan uygulamalar tarafından uygulanır.  
  
 Sunucu tarafı sağlayıcılar, arabirimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek sisteme sunarak işlem sınırları genelinde istemci uygulamalarıyla iletişim kurar ve bu da istemcilerden gelen istekleri üstlenir.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>UI Otomasyon sağlayıcısı kavramları  
 Bu bölüm, UI Otomasyon sağlayıcılarını uygulamak için anlamanız gereken bazı temel kavramların kısa açıklamalarını sunmaktadır.  
  
### <a name="elements"></a>Öğeler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeler, UI Otomasyonu istemcilerinin görebileceği [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] parçalardır. Örnek olarak uygulama pencereleri, bölmeler, düğmeler, araç ipuçları, liste kutuları ve liste öğeleri bulunur.  
  
### <a name="navigation"></a>Gezinti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeler, istemcilere bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı olarak sunulur. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir öğeden diğerine giderek ağacı oluşturur. Gezinti, her biri bir üst, eşdüzey öğe ve alt öğeye işaret eden her öğe için sağlayıcılar tarafından etkinleştirilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının istemci görünümü hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Görünümler  
 İstemci, aşağıdaki tabloda gösterildiği gibi üç ana görünümde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacını görebilir.  
  
|||  
|-|-|  
|Ham görünüm|Tüm öğeleri içerir.|  
|Denetim görünümü|Denetimler olan öğeleri içerir.|  
|İçerik görünümü|İçeriği olan öğeleri içerir.|  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının istemci görünümleri hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
 Bu, bir öğeyi içerik öğesi veya denetim öğesi olarak tanımlamak için sağlayıcı uygulamasının sorumluluğundadır. Denetim öğeleri de içerik öğeleri olabilir veya olmayabilir, ancak tüm içerik öğeleri denetim öğeleridir.  
  
### <a name="frameworks"></a>Çerçeveler  
 Çerçeve, ekranın bir alanında alt denetimleri, isabet sınamasını ve işlemeyi yöneten bir bileşendir. Örneğin, genellikle HWND olarak anılan bir Win32 penceresi, bir menü çubuğu, bir durum çubuğu ve düğmeler gibi birden çok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi içeren bir çerçeve işlevi görebilir.  
  
 Liste kutuları ve ağaç görünümleri gibi Win32 kapsayıcı denetimleri, alt öğeleri işlemek ve bunlar üzerinde isabet testi gerçekleştirmek için kendi kodlarını içerdiğinden çerçeveler olarak kabul edilir. Bunun aksine, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] liste kutusu çerçeve değildir, çünkü işleme ve isabet testi içeren [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pencere tarafından işlenir.  
  
 Bir uygulamadaki [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] farklı çerçevelerden oluşabilir. Örneğin, bir HWND uygulama penceresi, bir HWND içindeki Birleşik giriş kutusu gibi bir bileşeni içeren dinamik HTML (DHTML) içerebilir.  
  
### <a name="fragments"></a>Parçalar  
 Bir parça, belirli bir çerçeveden öğelerin tüm alt ağaclarından oluşur. Alt ağacın kök düğümündeki öğesine bir parça kökü denir. Bir parça kökünün bir üst öğesi yoktur, ancak genellikle bir Win32 penceresi (HWND), başka bir çerçeve içinde barındırılır.  
  
### <a name="hosts"></a>Konaklar  
 Her parçanın kök düğümü, genellikle Win32 penceresinde (HWND) bir öğede barındırılmalıdır. Özel durum, başka bir öğede barındırılmayan masaüsttür. Özel bir denetimin Konağı, uygulama penceresi veya üst düzey denetim grupları içerebilen herhangi bir pencere değil, denetimin kendisidir.  
  
 Bir parçanın ana bilgisayarı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmetleri sağlamak için önemli bir rol oynar. Parça köküne gezinmeyi sağlar ve özel sağlayıcının bunları uygulamak zorunda kalmaması için bazı varsayılan özellikleri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
