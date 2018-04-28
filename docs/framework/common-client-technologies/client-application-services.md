---
title: İstemci Uygulama Hizmetleri
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9532594f5f243faed28229388b9a6d597be57a7d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="client-application-services"></a><span data-ttu-id="379dc-102">İstemci Uygulama Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="379dc-102">Client Application Services</span></span>
<span data-ttu-id="379dc-103">İstemci uygulama hizmetleri kullanan Windows tabanlı uygulamalar oluşturmanızı kolaylaştırır [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] oturum açma, roller ve Microsoft ASP.NET 2.0 AJAX uzantılarında dahil profili uygulama hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="379dc-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="379dc-104">Bu hizmetler, birden çok Web ve Windows tabanlı uygulamalar kullanıcı bilgileri ve kullanıcı yönetimi işlevleri tek bir sunucudan paylaşmak için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="379dc-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="379dc-105">Örneğin, aşağıdaki görevleri gerçekleştirmek için bu hizmetleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="379dc-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="379dc-106">Bir kullanıcı kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="379dc-106">Authenticate a user.</span></span> <span data-ttu-id="379dc-107">Kimlik doğrulama hizmeti, bir kullanıcının kimliğini doğrulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379dc-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="379dc-108">Rol veya kimliği doğrulanmış bir kullanıcı rolleri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="379dc-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="379dc-109">Rol hizmeti, kullanıcı rolüne bağlı olarak, uygulamanızın kullanıcı arabirimi değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379dc-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="379dc-110">Örneğin, bir yönetici rolü olan kullanıcılar için ek özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="379dc-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="379dc-111">Sunucuda bulunan depolama ve erişim kullanıcı başına uygulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="379dc-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="379dc-112">Ayarları birden çok uygulama ve konumları arasında paylaşmak için Web ayarları hizmeti (Profil Hizmeti olarak da bilinir) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379dc-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="379dc-113">İstemci uygulama hizmetleri, uygulama yapılandırma dosyaları belirtebilirsiniz istemci hizmet sağlayıcıları üzerinden Web Hizmetleri genişletilebilirlik modeli yararlanın.</span><span class="sxs-lookup"><span data-stu-id="379dc-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="379dc-114">Bu hizmet sağlayıcıları bir ağ bağlantısı kullanılabilir olmadığında kimlik doğrulama, rolleri ve ayar verileri için yerel önbelleği kullanan çevrimdışı işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="379dc-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="379dc-115">Hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama bkz [ASP.NET uygulama hizmetleri genel bakış](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span><span class="sxs-lookup"><span data-stu-id="379dc-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="379dc-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="379dc-116">In This Section</span></span>  
 [<span data-ttu-id="379dc-117">İstemci Uygulama Servislerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="379dc-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="379dc-118">İstemci uygulama hizmet sağlayıcıları kullanılabilen özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="379dc-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="379dc-119">Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="379dc-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="379dc-120">Etkinleştirmek için Visual Studio Proje Tasarımcısı ve yapılandırma uygulama hizmetleri nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="379dc-120">Describes how to use the Visual Studio project designer to enable and configuration application services.</span></span> <span data-ttu-id="379dc-121">Ayrıca, App.config dosyasına karşılık gelen değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="379dc-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="379dc-122">Nasıl Yapılır: İstemci Uygulama Servisleri ile Kullanıcı Oturum Açma Adını Uygulama</span><span class="sxs-lookup"><span data-stu-id="379dc-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="379dc-123">Uygulamanızı bir istemci kimlik doğrulama hizmeti sağlayıcısı kullanacak şekilde yapılandırıldığında, bir kullanıcıyı doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="379dc-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="379dc-124">İzlenecek Yol: İstemci Uygulama Servislerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="379dc-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="379dc-125">Tek bir uygulama içinde tüm istemci uygulama hizmetleri özellikleri birleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="379dc-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="379dc-126">Bu kılavuz, uçtan uca yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="379dc-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="379dc-127">Örneğin, istemci uygulama hizmetleri test etmek için kullanabileceğiniz bir ASP.NET Web hizmeti uygulama oluşturmak yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="379dc-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="379dc-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="379dc-128">Reference</span></span>  
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
  
## <a name="see-also"></a><span data-ttu-id="379dc-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="379dc-129">See Also</span></span>  
 [<span data-ttu-id="379dc-130">ASP.NET uygulama hizmetleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="379dc-130">ASP.NET Application Services Overview</span></span>](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="379dc-131">Microsoft Ajax ile form kimlik doğrulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="379dc-131">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="379dc-132">Microsoft Ajax ile rolleri bilgileri kullanarak</span><span class="sxs-lookup"><span data-stu-id="379dc-132">Using Roles Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="379dc-133">Microsoft Ajax ile profil bilgilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="379dc-133">Using Profile Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="379dc-134">ASP.NET kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="379dc-134">ASP.NET Authentication</span></span>](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="379dc-135">[Yetkilendirme rollerini kullanarak yönetme](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="379dc-135">[Managing Authorization Using Roles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="379dc-136">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="379dc-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)
