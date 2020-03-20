---
title: İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 50d7921f1c63580248b562864f9c1f398d41c9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180251"
---
# <a name="client-side-ui-automation-provider-implementation"></a>İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Win32, Windows Forms ve [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Kullanıcı-ı UI öğeleri hakkındaki bilgileri istemcilere karşı ortaya çıkarır. Ancak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kendisi bu çerçevelerde var olan farklı denetim türleri ve bunlardan bilgi ayıklamak için gerekli olan teknikler hakkında farkında değildir. Bunun yerine, bu görevi sağlayıcı lar olarak adlandırılan nesnelere bırakır. Sağlayıcı belirli bir denetimden bilgi ayıklar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ve bu bilgileri ,daha sonra tutarlı bir şekilde istemciye sunar.  
  
 Sağlayıcılar sunucu tarafında veya istemci tarafında bulunabilir. Sunucu tarafı sağlayıcısı, denetimin kendisi tarafından uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]öğeleri, herhangi bir üçüncü taraf denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] göz önünde bulundurularak yazılmış olabilir gibi, sağlayıcıları uygulamak.  
  
 Ancak, Win32 ve Windows Formlar gibi eski [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]denetimler doğrudan desteklemez. Bu denetimler yerine istemci sürecinde var olan sağlayıcılar tarafından sunulur ve çapraz işlem iletişimini kullanarak denetimler hakkında bilgi alır; örneğin, windows iletilerini denetimlere ve denetimlerden izleyerek. Bu tür istemci tarafı sağlayıcıları bazen vekiller olarak adlandırılır.  
  
 Windows Vista, standart Win32 ve Windows Forms denetimleri için sağlayıcılar sağlar. Buna ek olarak, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] geri dönüş sağlayıcısı, başka bir sunucu tarafı sağlayıcısı veya proxy tarafından sunulan ancak Microsoft Etkin Erişilebilirlik uygulaması olan herhangi bir denetime kısmi destek sağlar. Tüm bu sağlayıcılar otomatik olarak yüklenir ve istemci uygulamaları tarafından kullanılabilir.  
  
 Win32 ve Windows Forms denetimleri için destek hakkında daha fazla bilgi [için, Standart Denetimler için Kullanıcı Arabirimi Otomasyon Desteği'ne](ui-automation-support-for-standard-controls.md)bakın.  
  
 Uygulamalar diğer istemci tarafı sağlayıcıları da kaydedebilir.  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>İstemci Tarafı Sağlayıcıları Dağıtma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yönetilen kod derlemesinde istemci tarafı sağlayıcıları bulmayı bekler. Bu derlemedeki ad alanı derlemeyle aynı ada sahip olmalıdır. Örneğin, ContosoProxies.dll adlı bir derleme ContosoProxies ad alanı içerir. Ad alanı içinde bir <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> sınıf oluşturun. Statik <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> alanın uygulanmasında, sağlayıcıları açıklayan bir <xref:System.Windows.Automation.ClientSideProviderDescription> dizi yapı oluşturun.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>İstemci Tarafı SağlayıcılarıN Kaydedilmesi ve Yapılandırılması  
 Dinamik bağlantı kitaplığındaki (DLL) istemci tarafı sağlayıcıları <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>arayarak yüklenir. Sağlayıcılardan yararlanmak için istemci uygulaması tarafından başka bir işlem gerekmemektedir.  
  
 Müşterinin kendi kodunda uygulanan sağlayıcılar kullanılarak <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>kaydedilir. Bu yöntem, bağımsız değişken <xref:System.Windows.Automation.ClientSideProviderDescription> olarak, her biri aşağıdaki özellikleri belirten bir dizi yapı yı alır:  
  
- Sağlayıcı nesnesini oluşturan bir geri arama işlevi.  
  
- Sağlayıcının hizmet edeceği denetimlerin sınıf adı.  
  
- Sağlayıcının hizmet edeceği uygulamanın görüntü adı (genellikle yürütülebilir dosyanın tam adı).  
  
- Sınıf adının hedef uygulamada bulunan pencere sınıfları ile nasıl eşleşildiğini yöneten bayraklar.  
  
 Son iki parametre isteğe bağlıdır. İstemci, farklı uygulamalar için farklı sağlayıcılar kullanmak istediğinde hedef uygulamanın görüntü adını belirtebilir. Örneğin, istemci, Birden Çok Görünüm deseni destekleyen bilinen bir uygulamada Win32 liste görünümü denetimi için bir sağlayıcı ve olmayan bilinen başka bir uygulamada benzer bir denetim için başka bir sağlayıcı kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](create-a-client-side-ui-automation-provider.md)
- [UI Otomasyon Sağlayıcıları İstemci Programına Uygulama](implement-ui-automation-providers-in-a-client-application.md)
