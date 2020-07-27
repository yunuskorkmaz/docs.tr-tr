---
title: İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
description: İstemci tarafı UI Otomasyon sağlayıcısı uygulamasını anlayın. İstemci tarafı sağlayıcılarının nasıl dağıtılacağını, kaydedeceğinizi ve yapılandırılacağını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 867293c00d0724e27f5163f3ae8be43aca30cfe8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164395"
---
# <a name="client-side-ui-automation-provider-implementation"></a>İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Birçok farklı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeve, Microsoft işletim sistemleri Içinde Win32, Windows Forms ve dahil olmak üzere kullanılıyor [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] . [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]istemciler için Kullanıcı arabirimi öğeleri hakkında bilgi gösterir. Ancak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bu çerçevelerde bulunan farklı denetim türlerini ve onlardan bilgi ayıklamak için gereken teknikleri kendi kendine tanıma sahip değildir. Bunun yerine, bu görevi sağlayıcılar adlı nesnelere bırakır. Sağlayıcı, belirli bir denetimdeki bilgileri ayıklar ve bu bilgileri öğesine [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sunar, böylece istemciye tutarlı bir şekilde sunulur.  
  
 Sağlayıcılar sunucu tarafında ya da istemci tarafında bulunabilir. Sunucu tarafı sağlayıcı, denetimin kendisi tarafından uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]öğeler, gibi, göz önünde bulundurularak yazılan üçüncü taraf denetimleri gibi sağlayıcıları uygular [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Ancak, Win32 ve Windows Forms gibi eski denetimler doğrudan desteklemez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Bu denetimler, istemci işleminde bulunan sağlayıcılar tarafından bunun yerine sunulur ve çapraz işlem iletişimini kullanarak denetimler hakkında bilgi elde eder; Örneğin, denetimlere ve denetimlerine ait Windows iletilerini izleyerek. Bu tür istemci tarafı sağlayıcılar bazen proxy olarak adlandırılır.  
  
 Windows Vista, standart Win32 ve Windows Forms denetimleri için sağlayıcılar sağlar. Ayrıca, bir geri dönüş sağlayıcısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] başka bir sunucu tarafı sağlayıcı veya proxy tarafından sunulmayan ancak Microsoft Etkin Erişilebilirlik uygulamasına sahip olan herhangi bir denetime kısmi destek verir. Bu sağlayıcıların tümü otomatik olarak yüklenir ve istemci uygulamaları tarafından kullanılabilir.  
  
 Win32 ve Windows Forms denetimleri desteği hakkında daha fazla bilgi için bkz. [standart denetimler Için UI Otomasyon desteği](ui-automation-support-for-standard-controls.md).  
  
 Uygulamalar diğer istemci tarafı sağlayıcılarını de kaydedebilir.  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>Istemci tarafı sağlayıcıları dağıtma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yönetilen kod derlemesinde istemci tarafı sağlayıcıları bulmayı bekler. Bu derlemedeki ad alanı derlemeyle aynı ada sahip olmalıdır. Örneğin, ContosoProxies.dll adlı bir derleme Contosoproxy ad alanını içerir. Ad alanı içinde bir sınıf oluşturun <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> . Statik alanı uygulamasında, <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> <xref:System.Windows.Automation.ClientSideProviderDescription> sağlayıcıları tanımlayan bir yapı dizisi oluşturun.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>Istemci tarafı sağlayıcıları kaydetme ve yapılandırma  
 Dinamik bağlantı kitaplığı (DLL) içindeki istemci tarafı sağlayıcılar, çağırarak yüklenir <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A> . Sağlayıcıları kullanabilmeniz için bir istemci uygulaması tarafından başka bir işlem yapılması gerekmez.  
  
 İstemcinin kendi kodunda uygulanan sağlayıcılar kullanılarak kaydedilir <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> . Bu yöntem <xref:System.Windows.Automation.ClientSideProviderDescription> , her biri aşağıdaki özellikleri belirten bir dizi yapıı bağımsız değişkeni olarak alır:  
  
- Sağlayıcı nesnesini oluşturan bir geri çağırma işlevi.  
  
- Sağlayıcının kullanacağı denetimlerin sınıf adı.  
  
- Sağlayıcının kullanacağı uygulamanın görüntü adı (genellikle yürütülebilir dosyanın tam adı).  
  
- Sınıf adının hedef uygulamada bulunan pencere sınıflarıyla nasıl eşleştiğini belirleyen bayraklar.  
  
 Son iki parametre isteğe bağlıdır. İstemci, farklı uygulamalar için farklı sağlayıcılar kullanmak istediğinde hedef uygulamanın görüntü adını belirtebilir. Örneğin, istemci, bilinen bir uygulamada birden çok görünüm modelini destekleyen ve başka bir bilinen uygulamadaki benzer bir denetim için bir Win32 liste görünümü denetimi için bir sağlayıcı kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma](create-a-client-side-ui-automation-provider.md)
- [UI Otomasyon Sağlayıcıları İstemci Programına Uygulama](implement-ui-automation-providers-in-a-client-application.md)
