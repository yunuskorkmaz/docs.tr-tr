---
title: "Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb5adec17f834687038b729a475fbcc0e2311c01
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Rol sağlayıcısı (birlikte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı) sağlayan bir özelliktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bir hesabı olan bir site oluşturmak için ve yetkilendirme için rolleri atanan kullanıcıların Web siteleri oluşturmak için geliştiriciler amaçlar. Bu özellik, herhangi bir kullanıcı sitesi olan bir hesap oluşturun ve site ve hizmetlerini özel erişim için oturum açın. Kullanıcıların bir Windows etki alanında hesaplarına sahip olmasını gerektiren Windows güvenliği aksine budur. Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) sağlayan herhangi bir kullanıcı site ve hizmetlerini kullanabilirsiniz.  
  
 Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı özelliği, bkz: [nasıl yapılır: ASP.NET üyelik sağlayıcıyı kullanacak](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 Rol sağlayıcı özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanır. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilir. Tümleşik olduğunda bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, kullanıcıların gerekir sağlamak için bir kullanıcı adı/parola birleşimini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygulaması. Etkinleştirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veritabanını kullanmak için bir örneğini oluşturun <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> sınıfı, Ayarla kendi <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğine <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>ve örnek olarak koleksiyonuna ekleyin <xref:System.ServiceModel.ServiceHost> hizmet barındırma.  
  
### <a name="to-configure-the-role-provider"></a>Rol sağlayıcısı yapılandırmak için  
  
1.  Web.config dosyasında altında <`system.web`> öğesi ekleme bir <`roleManager`> öğesi ve kümesi kendi `enabled` özniteliğini `true`.  
  
2.  Ayarlama `defaultProvider` özniteliğini `SqlRoleProvider`.  
  
3.  Alt öğesi olarak <`roleManager`> öğesi ekleme bir <`providers`> öğesi.  
  
4.  Alt öğesi olarak <`providers`> öğesi ekleme bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, ve `applicationName`, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>Hizmetini rol sağlayıcıyı kullanacak şekilde yapılandırmak için  
  
1.  Web.config dosyasına ekleyerek bir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.  
  
2.  Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesine <`system.ServiceModel`> öğesi.  
  
3.  Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.  
  
4.  Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ve kümesi `name` öznitelik için uygun bir değer.  
  
5.  Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için <`behavior`> öğesi.  
  
6.  Ayarlama `principalPermissionMode` özniteliğini `UseAspNetRoles`.  
  
7.  Ayarlama `roleProviderName` özniteliğini `SqlRoleProvider`. Aşağıdaki örnek, bir parça yapılandırmasının gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [Nasıl yapılır: ASP.NET üyelik sağlayıcısı kullanın](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
