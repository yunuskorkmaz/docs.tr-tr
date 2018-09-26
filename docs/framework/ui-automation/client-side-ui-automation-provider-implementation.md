---
title: İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 53773c51aef6b9530ed0b2cfaf0ef08cdb340ec2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205459"
---
# <a name="client-side-ui-automation-provider-implementation"></a>İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Birkaç farklı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeveleri olan kapsamında kullanımda [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] dahil olmak üzere işletim sistemlerini [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ve [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] istemciler için UI öğeleri hakkında bilgi gösterir. Ancak, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kendisi bu çerçeveleri alanında mevcut denetimleri farklı türlerdeki tanıma sahip ve için gereken teknik bilgi bunları ayıklayın. Bunun yerine, bu görev sağlayıcı olarak adlandırılan nesnelere bırakır. Bir sağlayıcı özel denetimden bilgisini ayıklar ve bu bilgileri uygulamalı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], daha sonra istemci için tutarlı bir şekilde sunar.  
  
 Sağlayıcıları, sunucu tarafında veya istemci tarafında bulunabilir. Sunucu tarafı sağlayıcı denetimi tarafından uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] öğeleri sağlayıcıları, uygulamak ile yazılmış tüm üçüncü taraf denetimleri gibi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] unutmayın.  
  
 Ancak, eski denetimleri olanlar gibi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] doğrudan desteklemez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Bu denetimler, bunun yerine mevcut istemci işlemini ve çapraz proses haberleşmesi kullanarak denetimleri hakkında bilgi edinme sağlayıcıları tarafından sunulan; Örneğin, windows iletilerini ve denetimlerinden izleyerek. Gibi istemci tarafı sağlayıcıları bazen proxy'leri çağrılır.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] Standart için sağlayıcılar sunar [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms denetimleri. Ayrıca, bir geri dönüş sağlayıcısı kısmi verir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteklemek için başka bir sunucu tarafı sağlayıcı tarafından sunulan değil herhangi bir denetimi veya proxy ancak sahip bir [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] uygulaması. Bu sağlayıcılar, otomatik olarak yüklenir ve istemci uygulamaları için kullanılabilir.  
  
 Yönelik destek hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] Windows Forms denetimleri görüp [UI Otomasyon desteği standart denetimler için](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Uygulamaları, ayrıca diğer istemci tarafı sağlayıcı kaydedebilir.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>İstemci tarafı sağlayıcı dağıtma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci tarafı sağlayıcı bir yönetilen kod derlemesine bulmayı bekler. Ad alanı bu derlemedeki derleme adıyla aynı olmalıdır. Örneğin, ContosoProxies.dll adlı bir derleme ContosoProxies ad alanı içerir. Ad alanı içinde oluşturun bir <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> sınıfı. Statik uygulamasında <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> alan, bir dizi oluşturma <xref:System.Windows.Automation.ClientSideProviderDescription> yapıları açıklayan sağlayıcıları.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Kaydetme ve istemci tarafı sağlayıcılarını yapılandırma  
 İstemci tarafı sağlayıcı belirtilen bölümler bir [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] çağrılarak yüklenen <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Başka bir işlem yapmak için bir istemci uygulaması tarafından gerekli sağlayıcılarından kullanın.  
  
 İstemcinin kendi kodda uygulanmış sağlayıcıları kullanarak kayıtlı <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Bu yöntem, bir dizi bağımsız değişken olarak alır <xref:System.Windows.Automation.ClientSideProviderDescription> yapıları, her biri aşağıdaki özellikleri belirtir:  
  
-   Sağlayıcı nesnesini oluşturan bir geri çağırma işlevi.  
  
-   Sağlayıcı hizmet denetim sınıfı adı.  
  
-   Sağlayıcı hizmet edeceği (genellikle yürütülebilir dosyanın tam ad) uygulama görüntü adı.  
  
-   Sınıf adı hedef uygulamada bulunan pencere sınıfları karşı nasıl eşleşen belirleyen bayrakları.  
  
 Son iki parametreler isteğe bağlıdır. Farklı uygulamalar için farklı sağlayıcıları kullanmak istediğinde, istemci hedef uygulama görüntü adını belirtebilirsiniz. Örneğin, istemci için bir sağlayıcı kullanabilirsiniz bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] liste görünümü denetimi daha önceden başka bir bilinen uygulamada benzer bir denetim için birden çok görünüm düzeni ve başka destekleyen bilinen bir uygulama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [UI Otomasyonu Sağlayıcıları Bir İstemci Programında Uygulama](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
