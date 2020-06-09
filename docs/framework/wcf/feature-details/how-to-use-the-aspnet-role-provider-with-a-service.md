---
title: 'Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595303"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="2f233-102">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="2f233-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="2f233-103">ASP.NET rol sağlayıcısı (ASP.NET üyelik sağlayıcısıyla birlikte), ASP.NET geliştiricilerin kullanıcıların bir sitesi olan bir hesap oluşturmalarına ve yetkilendirme amacıyla roller atanmasına olanak tanıyan Web siteleri oluşturmalarına olanak tanıyan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f233-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="2f233-104">Bu özellikle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="2f233-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="2f233-105">Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2f233-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="2f233-106">Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola birleşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2f233-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="2f233-107">Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2f233-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="2f233-108">ASP.NET üyelik sağlayıcısı özelliği hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma](how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2f233-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="2f233-109">Rol sağlayıcısı özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f233-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="2f233-110">Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2f233-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="2f233-111">Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f233-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="2f233-112">WCF 'yi veritabanını kullanmak üzere etkinleştirmek için, sınıfının bir örneğini oluşturmanız <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> , <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini olarak ayarlamanız <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> ve örneği, hizmeti barındıran davranış koleksiyonuna eklemeniz gerekir <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="2f233-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="2f233-113">Rol sağlayıcısını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2f233-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="2f233-114">Web. config dosyasında, < `system.web` > öğesi altında, bir < `roleManager` > öğesi ekleyin ve `enabled` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="2f233-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="2f233-115">`defaultProvider`Özniteliğini olarak ayarlayın `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="2f233-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="2f233-116"><> öğesi için alt öğe olarak `roleManager` bir <`providers`> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f233-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="2f233-117"><> öğesi için bir alt öğe olarak `providers` , aşağıdaki `add` örnekte gösterildiği gibi,,, ve gibi uygun değerlere ayarlanmış bir <> öğesi ekleyin: `name` , `type` , `connectionStringName` , ve `applicationName` .</span><span class="sxs-lookup"><span data-stu-id="2f233-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="2f233-118">Rol sağlayıcısını kullanmak için hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2f233-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="2f233-119">Web. config dosyasında bir [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f233-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="2f233-120">[\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)<> öğesine bir öğe ekleyin `system.ServiceModel` .</span><span class="sxs-lookup"><span data-stu-id="2f233-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="2f233-121">[\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md)<`behaviors`> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f233-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="2f233-122">Bir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f233-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="2f233-123">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)<`behavior`> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f233-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="2f233-124">`principalPermissionMode`Özniteliğini olarak ayarlayın `UseAspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="2f233-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="2f233-125">`roleProviderName`Özniteliğini olarak ayarlayın `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="2f233-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="2f233-126">Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f233-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f233-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f233-127">See also</span></span>

- [<span data-ttu-id="2f233-128">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2f233-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="2f233-129">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="2f233-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
