---
title: İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 9002b508602a219fac80770a27f628bb24150a6b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741771"
---
# <a name="client-side-ui-automation-provider-implementation"></a>İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Çeşitli farklı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeveleri Win32, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]ve [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]dahil olmak üzere Microsoft işletim sistemleri içinde kullanılıyor. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], istemcilerine yönelik kullanıcı arabirimi öğeleri hakkında bilgi sunar. Ancak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bu çerçevelerde bulunan farklı denetim türlerini ve onlardan bilgi ayıklamak için gereken teknikleri kendi kendine tanıma sahip değildir. Bunun yerine, bu görevi sağlayıcılar adlı nesnelere bırakır. Sağlayıcı, belirli bir denetimden bilgi ayıklar ve bu bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ve böylece istemciye tutarlı bir şekilde sunar.  
  
 Sağlayıcılar sunucu tarafında ya da istemci tarafında bulunabilir. Sunucu tarafı sağlayıcı, denetimin kendisi tarafından uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] öğeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] göz önünde bulundurularak yazılan üçüncü taraf denetimleri gibi sağlayıcıları uygular.  
  
 Ancak, Win32 ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] gibi eski denetimler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]doğrudan desteklemez. Bu denetimler, istemci işleminde bulunan sağlayıcılar tarafından bunun yerine sunulur ve çapraz işlem iletişimini kullanarak denetimler hakkında bilgi elde eder; Örneğin, denetimlere ve denetimlerine ait Windows iletilerini izleyerek. Bu tür istemci tarafı sağlayıcılar bazen proxy olarak adlandırılır.  
  
 Windows Vista, standart Win32 ve Windows Forms denetimleri için sağlayıcılar sağlar. Ayrıca, bir geri dönüş sağlayıcısı, başka bir sunucu tarafı sağlayıcı veya proxy tarafından sunulmayan ancak Microsoft Etkin Erişilebilirlik uygulamasına sahip olan herhangi bir denetime kısmi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği sağlar. Bu sağlayıcıların tümü otomatik olarak yüklenir ve istemci uygulamaları tarafından kullanılabilir.  
  
 Win32 ve Windows Forms denetimleri desteği hakkında daha fazla bilgi için bkz. [standart denetimler Için UI Otomasyon desteği](ui-automation-support-for-standard-controls.md).  
  
 Uygulamalar diğer istemci tarafı sağlayıcılarını de kaydedebilir.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Istemci tarafı sağlayıcıları dağıtma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], yönetilen kod derlemesinde istemci tarafı sağlayıcıları bulmayı bekler. Bu derlemedeki ad alanı derlemeyle aynı ada sahip olmalıdır. Örneğin, Contosoproxy. dll adlı bir derleme Contosoproxy ad alanını içerir. Ad alanı içinde <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> bir sınıf oluşturun. Statik <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> alanının uygulamasında, sağlayıcıları tanımlayan bir <xref:System.Windows.Automation.ClientSideProviderDescription> yapıları dizisi oluşturun.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Istemci tarafı sağlayıcıları kaydetme ve yapılandırma  
 Dinamik bağlantı kitaplığı (DLL) içindeki istemci tarafı sağlayıcılar <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>çağırarak yüklenir. Sağlayıcıları kullanabilmeniz için bir istemci uygulaması tarafından başka bir işlem yapılması gerekmez.  
  
 İstemcinin kendi kodunda uygulanan sağlayıcılar <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>kullanılarak kaydedilir. Bu yöntem, her biri aşağıdaki özellikleri belirten <xref:System.Windows.Automation.ClientSideProviderDescription> yapılarından oluşan bir dizi bağımsız değişken alır:  
  
- Sağlayıcı nesnesini oluşturan bir geri çağırma işlevi.  
  
- Sağlayıcının kullanacağı denetimlerin sınıf adı.  
  
- Sağlayıcının kullanacağı uygulamanın görüntü adı (genellikle yürütülebilir dosyanın tam adı).  
  
- Sınıf adının hedef uygulamada bulunan pencere sınıflarıyla nasıl eşleştiğini belirleyen bayraklar.  
  
 Son iki parametre isteğe bağlıdır. İstemci, farklı uygulamalar için farklı sağlayıcılar kullanmak istediğinde hedef uygulamanın görüntü adını belirtebilir. Örneğin, istemci, bilinen bir uygulamada birden çok görünüm modelini destekleyen ve başka bir bilinen uygulamadaki benzer bir denetim için bir Win32 liste görünümü denetimi için bir sağlayıcı kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](create-a-client-side-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıları Bir İstemci Programında Uygulama](implement-ui-automation-providers-in-a-client-application.md)
