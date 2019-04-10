---
title: 'Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 8f3fadc60645ef81d2683c63fda0ddd5bf24c982
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301145"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Rol sağlayıcısı (birlikte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı) sağlayan bir özelliktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştiriciler bir sitesinde bir hesap oluşturun ve yetkilendirme için rol atanmış kullanıcıların Web siteleri oluşturmak için amaçlar. Bu özellik, herhangi bir kullanıcı sitesine sahip bir hesabı oluşturabilir ve site ve Hizmetleri özel erişim için oturum açın. Kullanıcıların hesaplarını bir Windows etki alanına sahip olmasını gerektiren Windows Güvenlik aksine budur. Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) sağlayan herhangi bir kullanıcı, site ve hizmetlerini kullanabilirsiniz.  
  
 Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı özelliği bkz [nasıl yapılır: ASP.NET üyelik sağlayıcıyı kullanacak](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 Rol sağlayıcı özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanını kullanır. Windows Communication Foundation (WCF) geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilirsiniz. Kullanıcılar, bir WCF uygulamasına tümleştirildiğinde WCF istemci uygulaması için bir kullanıcı adı/parola birleşimini sağlamanız gerekir. WCF veritabanını kullanmak üzere etkinleştirmek için bir örneğini oluşturmak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> sınıfı olarak ayarlayın, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>ve davranışları için koleksiyonu örneği eklemek <xref:System.ServiceModel.ServiceHost> barındırma hizmeti.  
  
### <a name="to-configure-the-role-provider"></a>Rol sağlayıcısını yapılandırmak için  
  
1. Web.config dosyasında altında <`system.web`> öğesini ekleyin bir <`roleManager`> öğesi ve kümesi kendi `enabled` özniteliğini `true`.  
  
2. Ayarlama `defaultProvider` özniteliğini `SqlRoleProvider`.  
  
3. Alt öğesi olarak <`roleManager`> öğesini ekleyin bir <`providers`> öğesi.  
  
4. Alt öğesi olarak <`providers`> öğesini ekleyin bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, ve `applicationName`, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>Hizmeti rol sağlayıcıyı kullanacak şekilde yapılandırmak için  
  
1. Web.config dosyasında, ekleme bir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.  
  
2. Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesine <`system.ServiceModel`> öğesi.  
  
3. Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.  
  
4. Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ve kümesi `name` özniteliği için uygun bir değer.  
  
5. Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için <`behavior`> öğesi.  
  
6. Ayarlama `principalPermissionMode` özniteliğini `UseAspNetRoles`.  
  
7. Ayarlama `roleProviderName` özniteliğini `SqlRoleProvider`. Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.  
  
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
