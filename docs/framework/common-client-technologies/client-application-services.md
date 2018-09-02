---
title: İstemci Uygulama Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d58510240593f73ff761aa669035f28598006c10
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401589"
---
# <a name="client-application-services"></a>İstemci Uygulama Hizmetleri
İstemci uygulama hizmetleri kullanan Windows tabanlı uygulamalar oluşturmanızı kolaylaştırır [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] oturum açma, roller ve profil uygulaması hizmetlerini Microsoft ASP.NET 2.0 AJAX uzantıları dahil. Bu hizmetler, birden çok Web ve Windows tabanlı uygulamaların kullanıcı bilgileri ve kullanıcı yönetimi işlevleri tek bir sunucudan paylaşmasını sağlar. Örneğin, aşağıdaki görevleri gerçekleştirmek için bu hizmetlerin kullanabilirsiniz:  
  
-   Bir kullanıcı kimlik doğrulaması. Kimlik doğrulama hizmeti, bir kullanıcının kimliğini doğrulamak için kullanabilirsiniz.  
  
-   Veya kimliği doğrulanmış bir kullanıcının rol belirleyin. Rol hizmeti, kullanıcı rolüne bağlı olarak, uygulamanızın kullanıcı arabirimini değiştirmek için kullanabilirsiniz. Örneğin, bir yönetici rolü olan kullanıcılar için ek özellikler sağlar.  
  
-   Sunucudaki Store ve erişim kullanıcı başına uygulama ayarları. Ayarları birden çok uygulama ve konumları arasında paylaşmak için Web ayarları hizmeti (Profil Hizmeti olarak da bilinir) kullanabilirsiniz.  
  
 İstemci uygulama hizmetleri, uygulama yapılandırma dosyalarında belirttiğiniz istemci hizmet sağlayıcılar üzerinden Web Hizmetleri genişletilebilirlik modeli yararlanın. Bu hizmet sağlayıcıları, ağ bağlantısı kullanılabilir olmadığında, kimlik doğrulaması, roller ve ayar verileri için yerel önbellek kullanan çevrimdışı işlevselliğini içerir.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama hizmetleri [ASP.NET uygulama hizmetlerine genel bakış](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemci Uygulama Servislerine Genel Bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 İstemci uygulama hizmet sağlayıcıları kullanılabilen özellikleri açıklar.  
  
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Yapılandırma uygulama hizmetleri ve etkinleştirmek için Visual Studio Proje Tasarımcısı kullanmayı açıklar. Ayrıca, App.config dosyanıza karşılık gelen değişiklikleri açıklar.  
  
 [Nasıl Yapılır: İstemci Uygulama Servisleri ile Kullanıcı Oturum Açma Adını Uygulama](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Uygulamanızı bir istemci kimlik doğrulama hizmeti sağlayıcısı kullanmak için yapılandırıldığında bir kullanıcıyı doğrulamak açıklar.  
  
 [İzlenecek Yol: İstemci Uygulama Servislerini Kullanma](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Tek bir uygulamanın tüm istemci uygulama hizmetleri özelliklerini bir araya getirilebileceğini öğrenin açıklar. Bu izlenecek yol, uçtan uca yönergeler sağlar. Örneğin, istemci uygulama hizmetleri test etmek için kullanabileceğiniz bir ASP.NET Web hizmeti uygulaması oluşturmak yönergeler içerir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET uygulama hizmetlerine genel bakış](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Microsoft Ajax ile Forms kimlik doğrulaması kullanma](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Microsoft Ajax ile bilgi roller kullanma](https://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Microsoft Ajax ile profil bilgilerini kullanma](https://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET kimlik doğrulaması](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Rolleri kullanarak Yetkilendirme](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Uygulama Ayarlarına Genel Bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md)
