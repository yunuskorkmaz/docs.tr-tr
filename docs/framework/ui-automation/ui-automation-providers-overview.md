---
title: UI Otomasyon Sağlayıcılara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 40ad2eb09b4e3a8f78f493311cdb5c0da410943b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879421"
---
# <a name="ui-automation-providers-overview"></a>UI Otomasyon Sağlayıcılara Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 UI Otomasyonu sağlayıcıları UI otomasyon istemci uygulamaları ile iletişim kurmak denetimleri sağlar. Genel, her denetimi veya başka bir öğenin farklı bir [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] bir sağlayıcı tarafından temsil edilir. Sağlayıcı öğe hakkında bilgi gösterir ve isteğe bağlı olarak denetimle etkileşim kurmak istemci uygulamanın sağlayan denetim düzenleri uygular.  
  
 İstemci uygulamaları genellikle doğrudan sağlayıcıları ile çalışması gerekmez. Standart denetimler kullanan uygulamalarda çoğu [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] çerçeveleri için otomatik olarak sunulur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem. Özel denetimler uygulamak uygulamalarını de uygulamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları bu denetimleri ve istemci uygulamaları, onlara yönelik erişimi elde etmek için tüm özel adımlar gerek kalmaz.  
  
 Bu konu nasıl denetim geliştiricilerin uygulama genel bir bakış sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları, denetimler için özellikle [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Tür sağlayıcıları  
 UI Otomasyonu sağlayıcıları iki kategoriye ayrılır: istemci tarafı sağlayıcıları ve sunucu tarafı sağlayıcı.  
  
### <a name="client-side-providers"></a>İstemci tarafı sağlayıcı  
 İstemci tarafı sağlayıcı desteklemiyor veya tam desteklemez, bir uygulama ile iletişim kurmak için UI Otomasyon istemcileri tarafından uygulanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. İstemci tarafı sağlayıcı genellikle sunucu ile bir işlem sınırı arasında Windows iletileri gönderip iletişim kurar.  
  
 Çünkü denetimler için UI Otomasyon sağlayıcıları [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bu genel bakışta bunları kapsamaz uygulamalar işletim sisteminin bir parçası sağlanan ve istemci uygulamaları nadiren sahip kendi sağlayıcıları uygulamak Daha fazla.  
  
### <a name="server-side-providers"></a>Sunucu tarafı sağlayıcı  
 Sunucu tarafı sağlayıcı özel denetimleri veya başka bir kullanıcı Arabirimi Framework'e dayalı uygulamalar tarafından uygulanan [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Sunucu tarafı sağlayıcı işlemi sınırında arabirimlerine göstererek istemci uygulamaları ile iletişim kurmak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek sırayla istemcilerinden gelen istekleri veren sistem.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>UI Otomasyon sağlayıcı kavramları  
 Bu bölümde, bazı UI Otomasyon sağlayıcıları uygulamak için anlamanız gereken temel kavramları kısa açıklamaları sağlanır.  
  
### <a name="elements"></a>Öğeleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeler parçalarını [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , UI Otomasyon istemcileri için görünür. Windows uygulaması, bölmeleri, düğmeler, araç ipuçları, liste kutuları ve liste öğelerini verilebilir.  
  
### <a name="navigation"></a>Gezinti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri istemcilerine sunulur bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir öğeden diğerine giderek ağaç oluşturur. Gezinti, her biri bir üst öğe, eşdüzey ve alt öğeleri işaret edebilir, her öğe için sağlayıcıları tarafından etkinleştirilir.  
  
 İstemci görünümü hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Görünümler  
 Bir istemci görebilirsiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aşağıdaki tabloda gösterildiği gibi üç asıl görünümlerde ağaç.  
  
|||  
|-|-|  
|Ham görüntüle|Tüm öğeleri içerir.|  
|Denetim Görünüm|Denetim olan öğeleri içerir.|  
|İçerik görünümü|İçeriğe sahip öğeleri içerir.|  
  
 İstemci görünümleri hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Bir öğenin içerik öğesi veya bir denetim öğesi olarak tanımlamak için sağlayıcı uygulaması sorumluluğundadır. Denetim öğesi olabilir veya içerik öğeleri de olmayabilir ancak tüm içerik öğeleri denetim öğeleridir.  
  
### <a name="frameworks"></a>Çerçeveler  
 Bir çerçeve alt denetimler, isabet sınaması ve işleme ekranın bir alanda yöneten bir bileşenidir. Örneğin, bir [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] penceresi, genellikle bir HWND adlandırılan birden çok içeren bir çerçeve hizmet veren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir menü çubuğu, bir durum çubuğu ve düğmeler gibi öğeleri.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kapsayıcı liste kutuları gibi denetimleri ve ağaç görünümlerini üzerlerinde isabet-test çerçeveleri, alt öğelerini işlemek ve gerçekleştirmek için kendi kod içerdiklerinden olarak değerlendirilir. Bunun aksine, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] liste kutusu, çerçeve işleme ve isabet sınaması gerçekleştirilir için değil içeren [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] penceresi.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Bir uygulamada farklı çerçeveler meydana gelebilir. Örneğin, bir HWND uygulama penceresi içerebilir [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] sırayla içeren bir açılan kutunun içinde bir HWND gibi bir bileşen.  
  
### <a name="fragments"></a>Parçalar  
 Belirli bir çerçeve öğelerinden tam bir alt ağacı bir parçası olur. Bir parça kök öğe alt ağaç kök düğümü adı verilir. Bir parça kök bir üst öğesi yok, ancak bazı diğer Framework'te genellikle barındırılan bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] penceresi (HWND).  
  
### <a name="hosts"></a>Konaklar  
 Her parça kök düğümü bir öğedeki genellikle barındırılmalıdır bir [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] penceresi (HWND). Diğer herhangi bir öğenin barındırılmayan Masaüstü istisnadır. Özel denetim denetimin kendisinde değil, uygulama penceresinin ya da grup en üst düzey denetimleri içerebilen başka bir pencere HWND yöneticisidir.  
  
 Parçanın konak sağlayarak önemli bir rol oynar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Hizmetleri. Gezinti parça kök sağlar ve bunları uygulamak özel bir sağlayıcı yok, bazı varsayılan özellikleri sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
