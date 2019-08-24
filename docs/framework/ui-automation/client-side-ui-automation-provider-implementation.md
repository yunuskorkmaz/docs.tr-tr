---
title: İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 9079dfa03ab81bfa6875e43bfa8a6e5351e0a35d
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015110"
---
# <a name="client-side-ui-automation-provider-implementation"></a>İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Birçok farklı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeve,, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]ve [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]dahil olmak üzere [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]Microsoft işletim sistemleri içinde kullanılıyor. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]istemciler için Kullanıcı arabirimi öğeleri hakkında bilgi gösterir. Ancak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bu çerçevelerde bulunan farklı denetim türlerini ve onlardan bilgi ayıklamak için gereken teknikleri kendi kendine tanıma sahip değildir. Bunun yerine, bu görevi sağlayıcılar adlı nesnelere bırakır. Sağlayıcı, belirli bir denetimdeki bilgileri ayıklar ve bu bilgileri öğesine [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sunar, böylece istemciye tutarlı bir şekilde sunulur.  
  
 Sağlayıcılar sunucu tarafında ya da istemci tarafında bulunabilir. Sunucu tarafı sağlayıcı, denetimin kendisi tarafından uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]öğeler, gibi, göz önünde bulundurularak yazılan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üçüncü taraf denetimleri gibi sağlayıcıları uygular.  
  
 Ancak, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] gibi eski denetimler doğrudan desteklemez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Bu denetimler, istemci işleminde bulunan sağlayıcılar tarafından bunun yerine sunulur ve çapraz işlem iletişimini kullanarak denetimler hakkında bilgi elde eder; Örneğin, denetimlere ve denetimlerine ait Windows iletilerini izleyerek. Bu tür istemci tarafı sağlayıcılar bazen proxy olarak adlandırılır.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]Standart [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms denetimleri için sağlayıcıları sağlar. Ayrıca, bir geri dönüş sağlayıcısı, başka [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir sunucu tarafı sağlayıcı veya proxy tarafından sunulmayan ancak Microsoft Etkin Erişilebilirlik uygulamasına sahip olan herhangi bir denetime kısmi destek verir. Bu sağlayıcıların tümü otomatik olarak yüklenir ve istemci uygulamaları tarafından kullanılabilir.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] Ve Windows Forms denetimleri hakkında daha fazla bilgi için bkz. [standart denetimler için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Uygulamalar diğer istemci tarafı sağlayıcılarını de kaydedebilir.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Istemci tarafı sağlayıcıları dağıtma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yönetilen kod derlemesinde istemci tarafı sağlayıcıları bulmayı bekler. Bu derlemedeki ad alanı derlemeyle aynı ada sahip olmalıdır. Örneğin, Contosoproxy. dll adlı bir derleme Contosoproxy ad alanını içerir. Ad alanı içinde bir <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> sınıf oluşturun. Statik <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> alanı uygulamasında, sağlayıcıları tanımlayan bir <xref:System.Windows.Automation.ClientSideProviderDescription> yapı dizisi oluşturun.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Istemci tarafı sağlayıcıları kaydetme ve yapılandırma  
 Dinamik bağlantı kitaplığı (DLL) içindeki istemci tarafı sağlayıcılar, çağırarak <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>yüklenir. Sağlayıcıları kullanabilmeniz için bir istemci uygulaması tarafından başka bir işlem yapılması gerekmez.  
  
 İstemcinin kendi kodunda uygulanan sağlayıcılar kullanılarak <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>kaydedilir. Bu yöntem, her biri aşağıdaki özellikleri belirten bir <xref:System.Windows.Automation.ClientSideProviderDescription> dizi yapıı bağımsız değişkeni olarak alır:  
  
- Sağlayıcı nesnesini oluşturan bir geri çağırma işlevi.  
  
- Sağlayıcının kullanacağı denetimlerin sınıf adı.  
  
- Sağlayıcının kullanacağı uygulamanın görüntü adı (genellikle yürütülebilir dosyanın tam adı).  
  
- Sınıf adının hedef uygulamada bulunan pencere sınıflarıyla nasıl eşleştiğini belirleyen bayraklar.  
  
 Son iki parametre isteğe bağlıdır. İstemci, farklı uygulamalar için farklı sağlayıcılar kullanmak istediğinde hedef uygulamanın görüntü adını belirtebilir. Örneğin, istemci, bilinen bir uygulamada birden çok görünüm modelini [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] destekleyen bir liste görünümü denetimi için bir sağlayıcı kullanabilir ve başka bir bilinen uygulamadaki benzer bir denetim için başka bir şekilde.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıları Bir İstemci Programında Uygulama](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
