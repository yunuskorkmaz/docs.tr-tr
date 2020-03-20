---
title: 'Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184763"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="e2ff8-102">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="e2ff8-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="e2ff8-103">ASP.NET rol sağlayıcısı (ASP.NET üyelik sağlayıcısıyla birlikte), ASP.NET geliştiricilerin kullanıcıların bir siteyle hesap oluşturmasına ve yetkilendirme amacıyla roller atanmasına olanak tanıyan Web siteleri oluşturmasına olanak tanıyan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="e2ff8-104">Bu özellik sayesinde, herhangi bir kullanıcı siteile bir hesap kurabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="e2ff8-105">Bu, kullanıcıların windows etki alanında hesapları olmasını gerektiren Windows güvenliğinin tam tersidir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="e2ff8-106">Bunun yerine, kimlik bilgilerini (kullanıcı adı/parola kombinasyonu) sağlayan herhangi bir kullanıcı siteyi ve hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="e2ff8-107">Örnek bir uygulama için [Üyelik ve Rol Sağlayıcısı'na](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="e2ff8-108">ASP.NET üyelik sağlayıcısı özelliği hakkında daha fazla bilgi için [bkz: ASP.NET Üyelik Sağlayıcısı'nı kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)</span><span class="sxs-lookup"><span data-stu-id="e2ff8-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="e2ff8-109">Rol sağlayıcısı özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="e2ff8-110">Windows Communication Foundation (WCF) geliştiricileri bu özelliklerden güvenlik amacıyla yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="e2ff8-111">Bir WCF uygulamasına entegre edildiğinde, kullanıcıların WCF istemci uygulamasına bir kullanıcı adı/parola kombinasyonu sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="e2ff8-112">WCF'nin veritabanını kullanmasını sağlamak için sınıfın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> bir örneğini <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> oluşturmanız, özelliğini <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>"veya hizmeti barındıran <xref:System.ServiceModel.ServiceHost> davranışlar koleksiyonuna örneği eklemeniz gerekir."</span><span class="sxs-lookup"><span data-stu-id="e2ff8-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="e2ff8-113">Rol sağlayıcısını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e2ff8-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="e2ff8-114">Web.config dosyasında, `system.web` <> öğesi altında, `roleManager` bir <`enabled`> öğesi `true`ekleyin ve özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="e2ff8-115">Özniteliği `defaultProvider` `SqlRoleProvider`' ne göre ayarlayın</span><span class="sxs-lookup"><span data-stu-id="e2ff8-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="e2ff8-116"><`roleManager`> öğesine bir çocuk olarak, <`providers` bir> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="e2ff8-117"><`providers`> öğesine bir çocuk olarak, uygun değerlere ayarlanmış aşağıdaki öznitelikleri içeren <`add` bir> öğesi `name`ekleyin: , , `type` `connectionStringName`ve `applicationName`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="e2ff8-118">Rol sağlayıcısını kullanacak şekilde hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e2ff8-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="e2ff8-119">Web.config dosyasında, bir [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="e2ff8-120"><`system.ServiceModel`> öğesine [ \<davranış>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="e2ff8-121"><`behaviors`> öğesine [ \<bir hizmetDavranışı>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="e2ff8-122">Davranış [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin `name` ve özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="e2ff8-123"><`behavior`> öğesine [ \<bir hizmetYetkilendirme>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="e2ff8-124">Özniteliği `principalPermissionMode` `UseAspNetRoles`' ne göre ayarlayın</span><span class="sxs-lookup"><span data-stu-id="e2ff8-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="e2ff8-125">Özniteliği `roleProviderName` `SqlRoleProvider`' ne göre ayarlayın</span><span class="sxs-lookup"><span data-stu-id="e2ff8-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="e2ff8-126">Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e2ff8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2ff8-127">See also</span></span>

- [<span data-ttu-id="e2ff8-128">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="e2ff8-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="e2ff8-129">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e2ff8-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
