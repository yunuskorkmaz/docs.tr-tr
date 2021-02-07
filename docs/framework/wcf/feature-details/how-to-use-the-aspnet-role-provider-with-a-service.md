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
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma

ASP.NET rol sağlayıcısı (ASP.NET üyelik sağlayıcısıyla birlikte), ASP.NET geliştiricilerin kullanıcıların bir sitesi olan bir hesap oluşturmalarına ve yetkilendirme amacıyla roller atanmasına olanak tanıyan Web siteleri oluşturmalarına olanak tanıyan bir özelliktir. Bu özellikle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir. Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır. Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola birleşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.  
  
Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../samples/membership-and-role-provider.md). ASP.NET üyelik sağlayıcısı özelliği hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma](how-to-use-the-aspnet-membership-provider.md).  
  
Rol sağlayıcısı özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanır. Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir. Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir. WCF 'yi veritabanını kullanmak üzere etkinleştirmek için, sınıfının bir örneğini oluşturmanız <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> , <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini olarak ayarlamanız <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> ve örneği, hizmeti barındıran davranış koleksiyonuna eklemeniz gerekir <xref:System.ServiceModel.ServiceHost> .  
  
## <a name="configure-the-role-provider"></a>Rol sağlayıcısını yapılandırma  
  
1. Web.config dosyasında, <> öğesinin altında, `system.web` bir <`roleManager`> öğesi ekleyin ve `enabled` özniteliğini olarak ayarlayın `true` .  
  
2. `defaultProvider`Özniteliğini olarak ayarlayın `SqlRoleProvider` .  
  
3. <> öğesi için alt öğe olarak `roleManager` bir <`providers`> öğesi ekleyin.  
  
4. <> öğesi için bir alt öğe olarak `providers` , aşağıdaki `add` örnekte gösterildiği gibi,,, ve gibi uygun değerlere ayarlanmış bir <> öğesi ekleyin: `name` , `type` , `connectionStringName` , ve `applicationName` .  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Rol sağlayıcısını kullanmak için hizmeti yapılandırma  
  
1. Web.config dosyasında bir [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.  
  
2. [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)<> öğesine bir öğe ekleyin `system.ServiceModel` .  
  
3. [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md)<`behaviors`> öğesine ekleyin.  
  
4. Bir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.  
  
5. [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)<`behavior`> öğesine ekleyin.  
  
6. `principalPermissionMode`Özniteliğini olarak ayarlayın `UseAspNetRoles` .  
  
7. `roleProviderName`Özniteliğini olarak ayarlayın `SqlRoleProvider` . Aşağıdaki örnek, yapılandırmanın bir parçasını gösterir.  
  
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

- [Üyelik ve Rol Sağlayıcısı](../samples/membership-and-role-provider.md)
- [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](how-to-use-the-aspnet-membership-provider.md)
