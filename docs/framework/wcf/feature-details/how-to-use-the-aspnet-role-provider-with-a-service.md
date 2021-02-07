---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma'
title: 'Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 24bf9ad72d3634baf1d7120e4e60ccde5a4078a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734119"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="b7bdc-103">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="b7bdc-103">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="b7bdc-104">ASP.NET rol sağlayıcısı (ASP.NET üyelik sağlayıcısıyla birlikte), ASP.NET geliştiricilerin kullanıcıların bir sitesi olan bir hesap oluşturmalarına ve yetkilendirme amacıyla roller atanmasına olanak tanıyan Web siteleri oluşturmalarına olanak tanıyan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-104">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="b7bdc-105">Bu özellikle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-105">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="b7bdc-106">Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="b7bdc-107">Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola birleşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-107">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="b7bdc-108">Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b7bdc-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="b7bdc-109">ASP.NET üyelik sağlayıcısı özelliği hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma](how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b7bdc-109">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="b7bdc-110">Rol sağlayıcısı özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-110">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="b7bdc-111">Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="b7bdc-112">Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-112">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="b7bdc-113">WCF 'yi veritabanını kullanmak üzere etkinleştirmek için, sınıfının bir örneğini oluşturmanız <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> , <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini olarak ayarlamanız <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> ve örneği, hizmeti barındıran davranış koleksiyonuna eklemeniz gerekir <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-113">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="b7bdc-114">Rol sağlayıcısını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7bdc-114">Configure the role provider</span></span>  
  
1. <span data-ttu-id="b7bdc-115">Web.config dosyasında, <> öğesinin altında, `system.web` bir <`roleManager`> öğesi ekleyin ve `enabled` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-115">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="b7bdc-116">`defaultProvider`Özniteliğini olarak ayarlayın `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-116">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="b7bdc-117"><> öğesi için alt öğe olarak `roleManager` bir <`providers`> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-117">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="b7bdc-118"><> öğesi için bir alt öğe olarak `providers` , aşağıdaki `add` örnekte gösterildiği gibi,,, ve gibi uygun değerlere ayarlanmış bir <> öğesi ekleyin: `name` , `type` , `connectionStringName` , ve `applicationName` .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-118">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="b7bdc-119">Rol sağlayıcısını kullanmak için hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7bdc-119">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="b7bdc-120">Web.config dosyasında bir [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-120">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="b7bdc-121">[\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)<> öğesine bir öğe ekleyin `system.ServiceModel` .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-121">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="b7bdc-122">[\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md)<`behaviors`> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-122">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="b7bdc-123">Bir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-123">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="b7bdc-124">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)<`behavior`> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-124">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="b7bdc-125">`principalPermissionMode`Özniteliğini olarak ayarlayın `UseAspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-125">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="b7bdc-126">`roleProviderName`Özniteliğini olarak ayarlayın `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="b7bdc-126">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="b7bdc-127">Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-127">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7bdc-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7bdc-128">See also</span></span>

- [<span data-ttu-id="b7bdc-129">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b7bdc-129">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="b7bdc-130">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b7bdc-130">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
