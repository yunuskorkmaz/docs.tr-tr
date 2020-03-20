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
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma

ASP.NET rol sağlayıcısı (ASP.NET üyelik sağlayıcısıyla birlikte), ASP.NET geliştiricilerin kullanıcıların bir siteyle hesap oluşturmasına ve yetkilendirme amacıyla roller atanmasına olanak tanıyan Web siteleri oluşturmasına olanak tanıyan bir özelliktir. Bu özellik sayesinde, herhangi bir kullanıcı siteile bir hesap kurabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir. Bu, kullanıcıların windows etki alanında hesapları olmasını gerektiren Windows güvenliğinin tam tersidir. Bunun yerine, kimlik bilgilerini (kullanıcı adı/parola kombinasyonu) sağlayan herhangi bir kullanıcı siteyi ve hizmetlerini kullanabilir.  
  
Örnek bir uygulama için [Üyelik ve Rol Sağlayıcısı'na](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)bakın. ASP.NET üyelik sağlayıcısı özelliği hakkında daha fazla bilgi için [bkz: ASP.NET Üyelik Sağlayıcısı'nı kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
  
Rol sağlayıcısı özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanır. Windows Communication Foundation (WCF) geliştiricileri bu özelliklerden güvenlik amacıyla yararlanabilir. Bir WCF uygulamasına entegre edildiğinde, kullanıcıların WCF istemci uygulamasına bir kullanıcı adı/parola kombinasyonu sağlaması gerekir. WCF'nin veritabanını kullanmasını sağlamak için sınıfın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> bir örneğini <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> oluşturmanız, özelliğini <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>"veya hizmeti barındıran <xref:System.ServiceModel.ServiceHost> davranışlar koleksiyonuna örneği eklemeniz gerekir."  
  
## <a name="configure-the-role-provider"></a>Rol sağlayıcısını yapılandırma  
  
1. Web.config dosyasında, `system.web` <> öğesi altında, `roleManager` bir <`enabled`> öğesi `true`ekleyin ve özniteliğini ayarlayın.  
  
2. Özniteliği `defaultProvider` `SqlRoleProvider`' ne göre ayarlayın  
  
3. <`roleManager`> öğesine bir çocuk olarak, <`providers` bir> öğesi ekleyin.  
  
4. <`providers`> öğesine bir çocuk olarak, uygun değerlere ayarlanmış aşağıdaki öznitelikleri içeren <`add` bir> öğesi `name`ekleyin: , , `type` `connectionStringName`ve `applicationName`, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Rol sağlayıcısını kullanacak şekilde hizmeti yapılandırma  
  
1. Web.config dosyasında, bir [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.  
  
2. <`system.ServiceModel`> öğesine [ \<davranış>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.  
  
3. <`behaviors`> öğesine [ \<bir hizmetDavranışı>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.  
  
4. Davranış [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin `name` ve özniteliği uygun bir değere ayarlayın.  
  
5. <`behavior`> öğesine [ \<bir hizmetYetkilendirme>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) ekleyin.  
  
6. Özniteliği `principalPermissionMode` `UseAspNetRoles`' ne göre ayarlayın  
  
7. Özniteliği `roleProviderName` `SqlRoleProvider`' ne göre ayarlayın Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üyelik ve Rol Sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
