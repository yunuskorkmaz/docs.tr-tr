---
title: "İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cf8a054b832b1accdfa8e1d63b2d971a10f244b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="client-side-ui-automation-provider-implementation"></a>İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Birkaç farklı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeveler, içinde kullanımda [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] dahil olmak üzere işletim sistemlerini [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ve [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]istemciler için UI öğeleri hakkında bilgi gösterir. Ancak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kendisi bu çerçeveleri mevcut denetimleri farklı türdeki tanıma sahip ve için gereken teknikleri bilgi onlardan ayıklayın. Bunun yerine, bu görev sağlayıcı olarak adlandırılan nesnelere bırakır. Bir sağlayıcı bilgileri belirli bir denetimden ayıklar ve bu bilgileri aktarır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], o istemci için tutarlı bir şekilde gösterir.  
  
 Sağlayıcıları, sunucu tarafında veya istemci tarafı bulunabilir. Sunucu tarafı sağlayıcı denetimi tarafından uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]öğeleri uygulamak sağlayıcıları ile yazılmış herhangi bir üçüncü taraf denetim gibi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] unutmayın.  
  
 Ancak, eski denetimler de gibi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] doğrudan desteklemez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Bu denetimler, bunun yerine, istemci işlemini yok ve işlem içi iletişimi kullanarak denetimleri hakkında bilgi edinme sağlayıcıları tarafından sunulan; Örneğin, denetimleri windows ileti izleme tarafından. Bu tür istemci-tarafı sağlayıcıları bazen proxy'leri denir.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]standart sağlayıcıları sağlayan [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] kontrol eder. Ayrıca, bir geri dönüş sağlayıcısı kısmi verir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteklemek için başka bir sunucu tarafı sağlayıcı tarafından sunulmuyor herhangi bir denetimi veya proxy ancak sahip bir [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] uygulaması. Bu sağlayıcılar, otomatik olarak yüklenir ve istemci uygulamaları için kullanılabilir.  
  
 Desteği hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] denetimleri bkz [standart denetimler için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Uygulamaları, diğer istemci-tarafı sağlayıcıları da kaydedebilirsiniz.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>İstemci tarafı sağlayıcı dağıtma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yönetilen kod derlemede istemci tarafı Sağlayıcı bulmak bekliyor. Bu ad alanı derleme adıyla aynı olmalıdır. Örneğin, ContosoProxies.dll adlı bir derleme ContosoProxies ad alanı içerir. Ad alanı içinde oluşturma bir <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> sınıfı. Statik uygulamasında <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> alan, bir dizi oluşturma <xref:System.Windows.Automation.ClientSideProviderDescription> sağlayıcıları açıklayan yapıları.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Kaydetme ve istemci tarafı sağlayıcı yapılandırma  
 İstemci tarafı sağlayıcı bir [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] çağırarak yüklenen <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Başka bir eylem yapmak için bir istemci uygulaması tarafından gerekli sağlayıcıların kullanın.  
  
 İstemcinin kendi kodunda uygulanan sağlayıcılarını kullanarak kayıtlı <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Bu yöntem bağımsız değişken olarak bir dizi alır <xref:System.Windows.Automation.ClientSideProviderDescription> yapıları, her biri aşağıdaki özellikleri belirtir:  
  
-   Sağlayıcı nesnesi oluşturan bir geri çağırma işlevi.  
  
-   Sağlayıcı hizmet denetimleri sınıfı adı.  
  
-   Görüntü adı sağlayıcı görecek uygulamanın (genellikle yürütülebilir dosyasının tam adı).  
  
-   Sınıf adı hedef uygulamada bulunan pencere sınıfları karşı nasıl eşleştirildiği belirleyen bayrak.  
  
 Son iki parametreler isteğe bağlıdır. Farklı uygulamalar için farklı sağlayıcıları kullanmak istediğinde istemci hedef uygulama görüntü adını belirtebilir. Örneğin, istemci için bir sağlayıcı kullanabilirsiniz bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] liste görünümü denetimi için benzer bir denetim yok ve bilinen başka bir uygulama içinde birden çok görünüm düzeni ve başka destekler bilinen bir uygulama içinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci tarafı UI Otomasyon sağlayıcı oluşturma](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [UI Otomasyon sağlayıcıları istemci programına uygulama](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
