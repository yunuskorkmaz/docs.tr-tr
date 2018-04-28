---
title: İstemci Uygulama Hizmetlerine Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- client application services, classes
- client application services, about client application services
ms.assetid: f0a2da13-e282-4fd7-88a1-f9102c9aeab1
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b166dc273eed83660565d9b3bc6a70ffc85547fa
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="client-application-services-overview"></a>İstemci Uygulama Hizmetlerine Genel Bakış
İstemci uygulama hizmetleri sağlamak için Basitleştirilmiş erişim [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] oturum açma, roller ve Windows Forms ve Windows Presentation Foundation (WPF) uygulamalardan profili Hizmetleri. [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] Uygulama Hizmetleri, Microsoft ASP.NET 2.0 AJAX, içerdiği uzantıları bulunmaktadır [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] ve [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Bu hizmetler, birden çok Web ve Windows tabanlı uygulamalar kullanıcı bilgileri ve kullanıcı yönetimi işlevleri tek bir sunucudan paylaşmak için etkinleştirin.  
  
 İstemci uygulama hizmetleri, Windows tabanlı uygulamalar için aşağıdaki özellikleri etkinleştirmek için Web services genişletilebilirlik modeli takın istemci hizmeti sağlayıcıları içerir:  
  
-   Basit istemci yapılandırması. Etkinleştirin ve oturum açma, roller ve profil Hizmetleri Visual Studio Proje Tasarımcısı'nı kullanarak veya projenizin App.config dosyasında istemci hizmeti sağlayıcıları belirterek yapılandırın. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
-   Basit programlamasına. Etkin ve istemci uygulama hizmetleri yapılandırdıktan sonra hizmet sağlayıcılarının dolaylı olarak varolan aracılığıyla erişebilirsiniz [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] üyelik, roller ve uygulama ayarlarını sınıfları. Ayrıca doğrudan erişebilirsiniz [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] istemci uygulama hizmetleri uygulayan sınıflar. Bununla birlikte, çoğu durumda, doğrudan erişim gerekli değildir. İstemci uygulama hizmetleri sınıfları hakkında daha fazla bilgi için bu konunun "İstemci uygulama hizmetleri sınıfları" bölümüne bakın.  
  
-   Çevrimdışı Destek. Windows tabanlı uygulamalar genellikle bazen bağlı ortamlarda çalışmasına sahiptir. Uygulamanızı çevrimiçi olduğunda, istemci hizmeti sağlayıcıları uygulama çevrimdışı olduğunda kullanılacak sunucusundan alınan değerleri önbelleğe alır.  
  
-   Visual Studio uygulama ayarları Tasarımcısı ile tümleştirme. Projeniz Visual Studio'da ayarları eklediğinizde, istemci ayarlarını hizmet sağlayıcısı üzerinden erişilebilmesi için olan ayarları belirtebilirsiniz.  
  
 Aşağıdaki bölümlerde bu özellikler daha ayrıntılı açıklanmıştır. Hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama bkz [ASP.NET uygulama hizmetleri genel bakış](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="authentication"></a>Kimlik doğrulaması  
 İstemci uygulama hizmetleri aracılığıyla var olan bir kullanıcıyı doğrulamak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] kimlik doğrulama hizmeti. Bir kullanıcı Windows veya forms kimlik doğrulaması kullanarak doğrulayabilirsiniz. Windows kimlik doğrulamasını bir kullanıcı oturum açtığında bir bilgisayar veya etki alanı işletim sistemi tarafından sağlanan bir kullanıcı kimliği anlamına gelir. Genellikle, bir Kurumsal intranet üzerinde dağıtılan bir uygulama ile Windows kimlik doğrulamasını kullanır. Form kimlik doğrulaması, uygulamanızda oturum açma denetimleri içerir ve kimlik doğrulama sağlayıcısı alınan kimlik bilgilerini geçirmek anlamına gelir. Genellikle, Internet üzerinde dağıtılan bir uygulama ile form kimlik doğrulaması kullanır.  
  
 Bir kullanıcıyı doğrulamak için arama `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, uygulamanız için yapılandırılmış istemci Hizmet Sağlayıcısı'na erişir ve döndüren bir <xref:System.Boolean> kullanıcı geçerli olup olmadığını belirten değer. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri ile uygulama kullanıcı oturum açma](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
 Windows kimlik doğrulaması kullanırken, boş dizeler geçmesi gerekir veya `null` parametreleri olarak <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi. Windows kimlik doğrulaması kullanırken, bu yöntem çağrısı her zaman döndürülecek `true`.  
  
 Form kimlik doğrulaması ile <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi uzak hizmet kullanıcı kimliği doğrulanmış olup olmadığını belirten bir değer döndürür. Doğrulama başarılı olursa, kimlik doğrulama tanımlama bilgisi yerel sabit disk üzerinde depolanır. Bu tanımlama bilgisi ayarları hizmetler ve roller erişirken doğrulama doğrulamak için kullanılır.  
  
 Forms kimlik doğrulaması kullanırken, bir kullanıcı adı ve parola geçirebilirsiniz <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi. Boş dizeler geçebilen veya `null` bir kimlik sağlayıcısı kullanmak için parametre olarak. Bir kimlik sağlayıcısı sağlamak ve uygulama yapılandırmanızda belirten bir sınıftır. Bir kimlik sağlayıcısı sınıfı uygulamalıdır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> adlı tek bir yöntemi olan arabirimi <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>. Bir kimlik sağlayıcısı kullanarak birden çok uygulama arasında bir tek oturum açma iletişim kutusu paylaşmanıza olanak sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Uygulamanızı bir kimlik sağlayıcısı ile form kimlik doğrulaması kullanacak şekilde yapılandırdığınızda, boş dizeler geçmesi gerekir veya `null` parametreleri olarak <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi. Hizmet sağlayıcısı sonra çağıracak, <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> yöntem uygulaması. Genellikle, bir iletişim kutusu görüntüler ve doldurulan bir dönmek için bu yöntem gerçekleştireceksiniz <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> nesnesi.  
  
 Kimlik doğrulaması hakkında daha fazla bilgi için bkz: [ASP.NET kimlik doğrulaması](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1). Nasıl ayarlandığı hakkında bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] kimlik doğrulama hizmeti bkz [Microsoft Ajax ile form kimlik doğrulaması kullanarak](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
## <a name="roles"></a>Roller  
 İstemci uygulama hizmetleri varolan bir rol bilgilerini almak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] rol hizmeti. Geçerli, kimliği doğrulanmış kullanıcının belirli bir rolde olup olmadığını belirlemek için arama <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi <xref:System.Security.Principal.IPrincipal> başvuru alınan `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği. <xref:System.Security.Principal.IPrincipal.IsInRole%2A> Yöntemi rol adı bir parametre olarak alıp döndüren bir <xref:System.Boolean> geçerli kullanıcının belirtilen rolde olup olmadığını belirten değer. Bu yöntem döndürülecek `false` kullanıcı kimliği doğrulanmamış veya belirtilen rolde değil.  
  
 Nasıl ayarlandığı hakkında bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] rol hizmeti, bkz: [rolleri bilgilerle kullanarak Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d).  
  
## <a name="settings"></a>Ayarlar  
 İstemci uygulama hizmetleri mevcut bir kullanıcı uygulama ayarlarını almak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmeti. Web ayarları özelliği sağlanan uygulama ayarlarını özelliği ile tümleşir istemci uygulama hizmetleri [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]. Web ayarları almak için önce oluşturmak bir `Settings` sınıfı (olarak erişilen `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te) kullanarak projeniz için **ayarları** Visual Studio Proje Tasarımcısı'nın sekmesi. Üzerinde **ayarları** kullanabileceğiniz sekmesinde **yük Web ayarları** Web ayarları almak ve bunları oluşturulan için Ekle düğmesini `Settings` sınıfı. Tüm kimliği doğrulanmış kullanıcılara veya tüm anonim kullanıcılar tarafından kullanılmak üzere yapılandırılmış Web ayarlarını kullanabilirsiniz.  
  
 Uygulama ayarları hakkında daha fazla bilgi için bkz: [uygulama ayarlarına genel bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md). Visual Studio birinde oluşturmak yerine, kendi ayarları sınıf uygulama hakkında daha fazla bilgi için bkz: [nasıl yapılır: uygulama ayarları oluştur](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md). Nasıl ayarlandığı hakkında bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmet için bkz: [profil bilgilerle kullanarak Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61).  
  
## <a name="client-application-services-classes"></a>Sınıfları istemci uygulama hizmetleri  
 Aşağıdaki tabloda, istemci uygulama hizmetleri özelliği uygulayan sınıflar açıklanmaktadır.  
  
 Yalnızca birincil kimlik doğrulaması, rolleri ve ayarları özellikleri kullanan uygulamaların bu sınıfların doğrudan erişimi gerekmez. Bunun yerine, bu tür uygulamalar dolaylı olarak uygulama yapılandırması ve önceki bölümlerde açıklanan API'lerini kullanarak istemci uygulama servis sağlayıcılarının erişir. Doğrudan kullanıcı oturum kapatma ve çevrimdışı yeteneği gibi ek özellikler uygulamak için bu sınıfların erişir.  
  
> [!NOTE]
>  Tüm istemci uygulama hizmetleri zaman uyumlu apı'leridir. İstemci uygulama hizmetleri zaman uyumsuz davranışı doğrudan desteklemez.  
  
 İstemci uygulama servis sağlayıcılarının uygulamak veya standart genişletmek [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] türleri, ancak her üye ve özelliği bu türleri tarafından tanımlanan uygulayın. Örneğin, yeni kullanıcı oluşturmak ve rol üyeliğini yönetmek için bir kullanıcı yönetimi uygulaması uygulamak için istemci uygulama servis sağlayıcılarının kullanamazsınız. Bu işlev uygulamak için şu anda bir Web uygulaması ve sunucu tarafı kodu kullanmanız gerekir. Hangi üyeleri uygulanmadı belirlemek için bu tabloda bağlantıları erişebileceğiniz başvuru belgelerine bakın.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Web.ClientServices.ClientFormsIdentity>|Bu sınıf, form kimlik doğrulaması için kullanıcı kimliğini ve kimlik doğrulama tanımlama yönetir.<br /><br /> Bu sınıf doğrudan erişmek için birincil nedeni çağırmaktır <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> sessiz bir şekilde bir kullanıcı (örneğin, çevrimiçi çevrimdışı modundan geçerken) yeniden doğrular yöntemi.<br /><br /> Kullanıcı form kimlik doğrulaması kullanarak doğrulandıktan sonra bu sınıfının bir örneği alabilirsiniz <xref:System.Security.Principal.IPrincipal.Identity%2A> özelliği <xref:System.Security.Principal.IPrincipal> başvuru alınan aracılığıyla `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Web.ClientServices.ClientRolePrincipal>|Bu sınıf, kullanıcı rollerini yönetir.<br /><br /> Bu sınıf dolaylı olarak erişilemez durumda herhangi bir üye yok. Ancak, kullanıcının kimliği doğrulandıktan sonra bu sınıf üzerinden örneği erişebilir `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Web.ClientServices.ConnectivityStatus>|Bu sınıfın sağladığı `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> özelliği uygulamanızı çevrimdışı moda geçiş yapmak için kullanın.|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>|Bu sınıf, kullanıcı kimlik bilgilerini temsil eder.<br /><br /> Bu sınıf yalnızca dönüş değeri türü olarak kullanacağınız <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> uyguladığınızda yöntemi <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi.|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>|Bu sınıf, form kimlik doğrulaması için uzaktan kimlik doğrulama hizmeti erişimini yönetir.<br /><br /> Bu sınıf doğrudan erişmek için birincil nedeni kullanmaktır kendi <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> ve <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> tarafından temel uygulanmadı üyeleri <xref:System.Web.Security.MembershipProvider> sınıfı. Kullanarak hizmet konumu programlı olarak ayarlayabilirsiniz <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.ServiceUri%2A> özelliği.<br /><br /> Bu sınıf üzerinden örneğini almak `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>|Bu sınıf Windows kimlik doğrulaması yönetir.<br /><br /> Bu sınıf doğrudan erişmek için birincil nedeni çağırmaktır kendi <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider.Logout%2A> yöntemi. Oturum kapatma sonra kullanıcı yine Windows kimlik doğrulaması yapılacak, ancak uzak uygulama hizmetlerini erişemiyor.<br /><br /> Bu sınıf üzerinden örneğini almak `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Web.ClientServices.Providers.ClientRoleProvider>|Bu sınıf uzaktan rol hizmetine erişimi yönetir.<br /><br /> Bu sınıf erişmek için birincil nedeni çağırmaktır kendi <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> yöntemi. Bu, uygulamanızın sıfır rol hizmeti önbellek zaman aşımı değeri kullanmak üzere yapılandırılmışsa, yararlı olabilir. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Kullanarak hizmet konumu programlı olarak ayarlayabilirsiniz <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ServiceUri%2A> özelliği.<br /><br /> Bu sınıf üzerinden örneğini almak `static` <xref:System.Web.Security.Roles.Provider%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Web.ClientServices.Providers.ClientSettingsProvider>|Bu sınıf, Uzak Web ayarları hizmeti erişimini yönetir.<br /><br /> Bu sınıf erişmek için birincil işlemek için bir nedeni <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> olay. Kullanarak hizmet konumu programlı olarak ayarlayabilirsiniz <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.ServiceUri%2A> özelliği.|  
|<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>|Bu arabirim, daha önce bu konuda kimlik doğrulaması bölümünde açıklandığı gibi kullanıcı kimlik doğrulama bilgilerini almak, uygulamanız için dolaylı bir yol sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).|  
|<xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>|Bu sınıfın sağladığı bir <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs.FailedSettingsList%2A> özelliği içinde kullanmak için bir <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> olay işleyicisi.|  
|<xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>|Bu sınıfın sağladığı bir <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs.UserName%2A> özelliği içinde kullanmak için bir <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> olay işleyicisi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Uygulama Servisleri](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Nasıl Yapılır: İstemci Uygulama Servisleri ile Kullanıcı Oturum Açma Adını Uygulama](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [İzlenecek Yol: İstemci Uygulama Servislerini Kullanma](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [ASP.NET uygulama hizmetleri genel bakış](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Microsoft Ajax ile form kimlik doğrulaması kullanma](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Microsoft Ajax ile rolleri bilgileri kullanarak](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Microsoft Ajax ile profil bilgilerini kullanma](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET kimlik doğrulaması](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Yetkilendirme rollerini kullanarak yönetme](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  
 [Oluşturma ve uygulama hizmetleri veritabanına SQL Server için yapılandırma](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
