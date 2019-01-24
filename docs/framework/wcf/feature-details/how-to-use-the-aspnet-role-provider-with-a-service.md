---
title: 'Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 0ad581a6967c759095d85d946a8557b47a075355
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658240"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="47b2b-102">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="47b2b-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="47b2b-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Rol sağlayıcısı (birlikte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı) sağlayan bir özelliktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştiriciler bir sitesinde bir hesap oluşturun ve yetkilendirme için rol atanmış kullanıcıların Web siteleri oluşturmak için amaçlar.</span><span class="sxs-lookup"><span data-stu-id="47b2b-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="47b2b-104">Bu özellik, herhangi bir kullanıcı sitesine sahip bir hesabı oluşturabilir ve site ve Hizmetleri özel erişim için oturum açın.</span><span class="sxs-lookup"><span data-stu-id="47b2b-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="47b2b-105">Kullanıcıların hesaplarını bir Windows etki alanına sahip olmasını gerektiren Windows Güvenlik aksine budur.</span><span class="sxs-lookup"><span data-stu-id="47b2b-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="47b2b-106">Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) sağlayan herhangi bir kullanıcı, site ve hizmetlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47b2b-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="47b2b-107">Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="47b2b-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="47b2b-108">Hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı özelliği bkz [nasıl yapılır: ASP.NET üyelik sağlayıcıyı kullanacak](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="47b2b-108">For more information about the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="47b2b-109">Rol sağlayıcı özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="47b2b-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="47b2b-110">Windows Communication Foundation (WCF) geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47b2b-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="47b2b-111">Kullanıcılar, bir WCF uygulamasına tümleştirildiğinde WCF istemci uygulaması için bir kullanıcı adı/parola birleşimini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47b2b-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="47b2b-112">WCF veritabanını kullanmak üzere etkinleştirmek için bir örneğini oluşturmak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> sınıfı olarak ayarlayın, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>ve davranışları için koleksiyonu örneği eklemek <xref:System.ServiceModel.ServiceHost> barındırma hizmeti.</span><span class="sxs-lookup"><span data-stu-id="47b2b-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="47b2b-113">Rol sağlayıcısını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="47b2b-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="47b2b-114">Web.config dosyasında altında <`system.web`> öğesini ekleyin bir <`roleManager`> öğesi ve kümesi kendi `enabled` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="47b2b-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="47b2b-115">Ayarlama `defaultProvider` özniteliğini `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="47b2b-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="47b2b-116">Alt öğesi olarak <`roleManager`> öğesini ekleyin bir <`providers`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="47b2b-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="47b2b-117">Alt öğesi olarak <`providers`> öğesini ekleyin bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, ve `applicationName`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="47b2b-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="47b2b-118">Hizmeti rol sağlayıcıyı kullanacak şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="47b2b-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="47b2b-119">Web.config dosyasında, ekleme bir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="47b2b-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="47b2b-120">Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesine <`system.ServiceModel`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="47b2b-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="47b2b-121">Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="47b2b-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="47b2b-122">Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ve kümesi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="47b2b-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="47b2b-123">Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için <`behavior`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="47b2b-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="47b2b-124">Ayarlama `principalPermissionMode` özniteliğini `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="47b2b-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="47b2b-125">Ayarlama `roleProviderName` özniteliğini `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="47b2b-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="47b2b-126">Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="47b2b-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47b2b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47b2b-127">See also</span></span>
- [<span data-ttu-id="47b2b-128">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="47b2b-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="47b2b-129">Nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="47b2b-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
