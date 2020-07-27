---
title: UI Otomasyon Sağlayıcılara Genel Bakış
description: Denetimlerin UI Otomasyonu istemci uygulamalarıyla iletişim kurmasına izin veren UI Otomasyon sağlayıcılarına genel bakış bölümüne bakın. Sağlayıcı türlerini ve sağlayıcı kavramlarını gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 08b6a199a98fb22f197ca0cf8a0268e5439aaf41
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163248"
---
# <a name="ui-automation-providers-overview"></a>UI Otomasyon Sağlayıcılara Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 UI Otomasyon sağlayıcıları, kullanıcıların UI Otomasyonu istemci uygulamalarıyla iletişim kurmasını sağlar. Genel olarak, içindeki her denetim veya diğer ayrı öğe [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] bir sağlayıcı tarafından temsil edilir. Sağlayıcı, öğesi hakkında bilgi gösterir ve isteğe bağlı olarak, istemci uygulamanın denetimle etkileşime geçmesini sağlayan denetim düzenlerini uygular.  
  
 İstemci uygulamalarının genellikle doğrudan sağlayıcılarıyla çalışması gerekmez. Win32, Windows Forms veya çerçeveleri kullanan uygulamalardaki Standart denetimlerin çoğu [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] otomatik olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sisteme sunulur. Özel denetimleri uygulayan uygulamalar da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bu denetimler için sağlayıcıları uygulayabilir ve istemci uygulamalarının bunlara erişim kazanmak için özel adımlar yapması gerekmez.  
  
 Bu konu, denetim geliştiricilerinin sağlayıcıları nasıl uygulayacağından ilgili bir genel bakış sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . özellikle de Windows Forms ve Win32 Windows denetimleri için.  
  
<a name="Types_of_Providers"></a>
## <a name="types-of-providers"></a>Sağlayıcı türleri  
 UI Otomasyonu sağlayıcıları iki kategoriye ayrılır: istemci tarafı sağlayıcılar ve sunucu tarafı sağlayıcılar.  
  
### <a name="client-side-providers"></a>İstemci tarafı sağlayıcıları  
 İstemci tarafı sağlayıcılar, Kullanıcı Arabirimi Otomasyonu istemcileri tarafından desteklenmeyen veya tam olarak desteklenmeyen bir uygulamayla iletişim kuracak şekilde uygulanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . İstemci tarafı sağlayıcılar, genellikle Windows iletileri gönderip alarak işlem sınırının tamamında sunucusuyla iletişim kurar.  
  
 Win32, Windows Forms veya uygulamalar 'daki denetimler için UI Otomasyon sağlayıcıları [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] işletim sisteminin bir parçası olarak sağlandığı için, istemci uygulamalarının nadiren kendi sağlayıcılarını uygulaması gerekir ve bu genel bakış bunları daha fazla kapsamaz.  
  
### <a name="server-side-providers"></a>Sunucu tarafı sağlayıcıları  
 Sunucu tarafı sağlayıcılar, özel denetimler veya Win32, Windows Forms veya dışında bir UI çerçevesini temel alan uygulamalar tarafından uygulanır [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] .  
  
 Sunucu tarafı sağlayıcılar, istemcileri çekirdek sisteme sunarak işlem sınırında istemci uygulamalarıyla iletişim kurar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bu da istemcilerden gelen istekleri üstlenir.  
  
<a name="AutomationProviderConcepts"></a>
## <a name="ui-automation-provider-concepts"></a>UI Otomasyon sağlayıcısı kavramları  
 Bu bölüm, UI Otomasyon sağlayıcılarını uygulamak için anlamanız gereken bazı temel kavramların kısa açıklamalarını sunmaktadır.  
  
### <a name="elements"></a>Öğeler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeler, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] UI Otomasyonu istemcilerinin görebileceği parçalarından oluşur. Örnek olarak uygulama pencereleri, bölmeler, düğmeler, araç ipuçları, liste kutuları ve liste öğeleri bulunur.  
  
### <a name="navigation"></a>Gezinti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeler, istemcilere ağaç olarak gösterilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bir öğeden diğerine giderek ağacı oluşturur. Gezinti, her biri bir üst, eşdüzey öğe ve alt öğeye işaret eden her öğe için sağlayıcılar tarafından etkinleştirilir.  
  
 Ağacın istemci görünümü hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Görünümler  
 Bir istemci, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Aşağıdaki tabloda gösterildiği gibi, ağacı üç ana görünümde görüntüleyebilir.  
  
|||  
|-|-|  
|Ham görünüm|Tüm öğeleri içerir.|  
|Denetim görünümü|Denetimler olan öğeleri içerir.|  
|İçerik görünümü|İçeriği olan öğeleri içerir.|  
  
 Ağacın istemci görünümleri hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
 Bu, bir öğeyi içerik öğesi veya denetim öğesi olarak tanımlamak için sağlayıcı uygulamasının sorumluluğundadır. Denetim öğeleri de içerik öğeleri olabilir veya olmayabilir, ancak tüm içerik öğeleri denetim öğeleridir.  
  
### <a name="frameworks"></a>Çerçeveler  
 Çerçeve, ekranın bir alanında alt denetimleri, isabet sınamasını ve işlemeyi yöneten bir bileşendir. Örneğin, genellikle HWND olarak anılan bir Win32 penceresi, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü çubuğu, bir durum çubuğu ve düğmeler gibi birden çok öğe içeren bir çerçeve işlevi görebilir.  
  
 Liste kutuları ve ağaç görünümleri gibi Win32 kapsayıcı denetimleri, alt öğeleri işlemek ve bunlar üzerinde isabet testi gerçekleştirmek için kendi kodlarını içerdiğinden çerçeveler olarak kabul edilir. Bunun aksine, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] liste kutusu çerçeve değildir, çünkü işleme ve isabet testi içeren pencere tarafından işlenir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] .  
  
 Uygulamasında [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir uygulama farklı çerçevelerden oluşabilir. Örneğin, bir HWND uygulama penceresi, bir HWND içindeki Birleşik giriş kutusu gibi bir bileşeni içeren dinamik HTML (DHTML) içerebilir.  
  
### <a name="fragments"></a>Fragments  
 Bir parça, belirli bir çerçeveden öğelerin tüm alt ağaclarından oluşur. Alt ağacın kök düğümündeki öğesine bir parça kökü denir. Bir parça kökünün bir üst öğesi yoktur, ancak genellikle bir Win32 penceresi (HWND), başka bir çerçeve içinde barındırılır.  
  
### <a name="hosts"></a>Ana bilgisayarlar  
 Her parçanın kök düğümü, genellikle Win32 penceresinde (HWND) bir öğede barındırılmalıdır. Özel durum, başka bir öğede barındırılmayan masaüsttür. Özel bir denetimin Konağı, uygulama penceresi veya üst düzey denetim grupları içerebilen herhangi bir pencere değil, denetimin kendisidir.  
  
 Bir parçanın ana bilgisayarı, hizmetleri sağlamak için önemli bir rol oynar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Parça köküne gezinmeyi sağlar ve özel sağlayıcının bunları uygulamak zorunda kalmaması için bazı varsayılan özellikleri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
