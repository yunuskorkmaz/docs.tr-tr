---
title: "UI Otomasyon Sağlayıcılara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
caps.latest.revision: "38"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dc5cb5749bbfe06fd3a1bbe3537b28c7bbfa295d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-providers-overview"></a>UI Otomasyon Sağlayıcılara Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 UI Otomasyon sağlayıcılar denetimler UI otomasyon istemci uygulamaları ile iletişim kurmasına olanak sağlar. Genel, her denetim veya diğer ayrı öğesinde bir [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] bir sağlayıcı tarafından temsil edilen. Sağlayıcı öğesi hakkında bilgi gösterir ve isteğe bağlı olarak istemci uygulamanın denetimi ile etkileşimli denetim düzenleri uygular.  
  
 İstemci uygulamaları genellikle doğrudan sağlayıcıları ile çalışmak zorunda değildir. Standart denetimler kullanan uygulamalarda çoğu [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] çerçeveler için otomatik olarak sunulur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem. Özel denetimler uygulamak uygulamalarını de uygulamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları bu denetimleri ve istemci uygulamaları için bunları erişim kazanmak için tüm özel adımlar gerekmez.  
  
 Bu konuda nasıl denetimi geliştiricileri uygulamak genel bir bakış sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimler için özellikle sağlayıcıları [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Sağlayıcı türü  
 UI Otomasyon sağlayıcılar iki kategoriye ayrılır: istemci-tarafı sağlayıcıları ve sunucu tarafı sağlayıcıları.  
  
### <a name="client-side-providers"></a>İstemci tarafı sağlayıcı  
 İstemci tarafı sağlayıcı desteklemiyor veya tam olarak desteklemez, bir uygulama ile iletişim kurmak için UI Otomasyon istemcileri tarafından uygulanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. İstemci-tarafı sağlayıcıları genellikle iletişim sunucuyla işlem sınırından gönderme ve alma [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] iletileri.  
  
 Çünkü denetimler için UI Otomasyon sağlayıcılar [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)], veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, işletim sisteminin bir parçası sağlanır, istemci uygulamaları kendi sağlayıcıları uygulamak için nadiren sahip ve bu genel bakışta bunları kapsamaz Daha fazla.  
  
### <a name="server-side-providers"></a>Sunucu tarafı sağlayıcıları  
 Sunucu tarafı sağlayıcıları özel denetimler veya başka bir kullanıcı Arabirimi Framework'e dayalı uygulamalar tarafından uygulanır [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)], veya [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Sunucu tarafı sağlayıcıları işlem sınırından arabirimlerine göstererek istemci uygulamaları ile iletişim kurmak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek sırayla istemcilerinden gelen istekleri hizmet veren sistem.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>UI Otomasyon sağlayıcı kavramları  
 Bu bölümde bazı UI Otomasyon sağlayıcılar uygulamak için anlamanız gereken temel kavramları kısa açıklamaları.  
  
### <a name="elements"></a>Öğeleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeleridir parçalarını [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , UI Otomasyon istemcileri için görünür. Örnek uygulama windows, bölmeleri, düğmeleri, araç ipuçları, liste kutuları ve liste öğeleri içerir.  
  
### <a name="navigation"></a>Gezinme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]öğeleri istemcilere açığa bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]başka bir öğeden giderek ağaç oluşturur. Gezinti sağlayıcıları her biri bir üst eşdüzey ve alt öğeleri için işaret edebilir, her bir öğe için etkinleştirilir.  
  
 İstemci görünümü hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Görünümler  
 Bir istemci görebilirsiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aşağıdaki tabloda gösterildiği gibi üç asıl görünümlerde ağacı.  
  
|||  
|-|-|  
|Ham görünümü|Tüm öğeleri içerir.|  
|Denetim Görünüm|Denetimler öğeleri içerir.|  
|İçerik görünümü|İçeriğe sahip öğeleri içerir.|  
  
 İstemci görünümleri hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Öğenin içerik öğesi ya da Denetim öğesi tanımlamak için sağlayıcı uygulaması sorumluluğundadır. Denetim öğeleri olabilir ya da içerik öğeleri olmayabilir, ancak tüm içerik öğeleri denetim öğelerdir.  
  
### <a name="frameworks"></a>çerçeveler  
 Bir çerçeve alt denetimler, vuruş sınaması ve işleme ekran bir bölgede yöneten bir bileşenidir. Örneğin, bir [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] penceresinde, genellikle bir HWND adlandırılan birden çok içeren bir çerçeve hizmet verebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü çubuğunda, durum çubuğu ve düğmeleri gibi.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]liste kutuları gibi kapsayıcı denetimleri ve ağaç görünümlerini isabet üzerlerinde sınama çerçeveleri, alt öğeleri oluşturma ve gerçekleştirmek için kendi kodlarını içerdiklerinden olduğu kabul edilir. Bunun aksine, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] liste kutusu, çerçeve işleme ve isabet test gerçekleştirilir için değil içeren [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] penceresi.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Farklı çerçeveleri yapılabilmesi için bir uygulama. Örneğin, bir HWND uygulama penceresi içerebilir [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] HWND açılan kutuda gibi bir bileşen sırayla içerir.  
  
### <a name="fragments"></a>Parçaları  
 Bir tam alt ağacını belirli çerçeveden öğelerinin bir parçası olur. Alt ağacı kök düğümü konumundaki öğe, bir parça kök adı verilir. Parça kök bir üst öğesi yok, ancak bazı diğer Framework'te genellikle barındırılan bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] penceresi (HWND).  
  
### <a name="hosts"></a>Ana bilgisayarlar  
 Her parçasının kök düğümünün bir öğedeki genellikle barındırılmalıdır bir [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] penceresi (HWND). Başka bir öğenin barındırılmayan Masaüstü istisnadır. Özel bir denetim denetimi kendisinde değil uygulama penceresi veya üst düzey denetim gruplarını içerebilir başka bir pencere HWND yöneticisidir.  
  
 Konak bir parça sağlayarak önemli bir rol oynar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Hizmetleri. Parça kök gezinme sağlar ve böylece özel sağlayıcı uygulamadan yok bazı varsayılan özellikleri sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
