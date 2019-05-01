---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 8011b026e857dd6e5815ef7da00c1c33db8b5b4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038720"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Üyelik sağlayıcısı sağlayan bir özelliktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştiricilerin benzersiz kullanıcı adı ve parola birleşimlerini oluşturmak için kullanıcıların Web siteleri oluşturun. Bu özelliği sayesinde, herhangi bir kullanıcı sitesine sahip bir hesabı oluşturabilir ve site ve Hizmetleri özel erişim için oturum açın. Kullanıcıların hesaplarını bir Windows etki alanına sahip olmasını gerektiren Windows Güvenlik aksine budur. Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) karşılayan herhangi bir kullanıcı, site ve hizmetlerini kullanabilirsiniz.  
  
 Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Kullanma hakkında bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcı özelliği bkz [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Üyelik özelliği, kullanıcı bilgilerini depolamak için SQL Server veritabanı kullanma gerektirir. Bu özellik ayrıca parolasını unutmuş kullanıcılar soru sormak için yöntemler içerir.  
  
 Windows Communication Foundation (WCF) geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilirsiniz. Bir WCF uygulamaya entegre edildiğinde, kullanıcılar WCF istemci uygulaması için bir kullanıcı adı/parola birleşimini sağlamanız gerekir. WCF hizmetine veri aktarmak için kullanıcı adı/parola kimlik bilgileri gibi destekleyen bir bağlama kullanın <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) ve istemci kimlik bilgisi türü içinayarlayın`UserName`. Hizmet WCF güvenlik kullanıcı adı ve parolasına dayalı kullanıcının kimliğini doğrular ve ayrıca tarafından belirtilen rol atar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol.  
  
> [!NOTE]
>  WCF kullanıcı adı/parola birleşimleri veritabanıyla veya diğer kullanıcı bilgilerini doldurmak için bir yöntem sağlamaz.  
  
### <a name="to-configure-the-membership-provider"></a>Üyelik sağlayıcısı yapılandırmak için  
  
1. Web.config dosyasında altında <`system.web`> öğesi oluşturmak bir <`membership`> öğesi.  
  
2. Altında `<membership>` öğesi oluşturmak bir `<providers>` öğesi.  
  
3. Alt öğesi olarak <`providers`> öğesini ekleyin bir `<clear />` sağlayıcıları koleksiyonunu temizlemek için öğesi.  
  
4. Altında `<clear />` öğesi oluşturmak bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, ve `passwordFormat`. `name` Özniteliği kullanılır daha sonra yapılandırma dosyasındaki bir değer olarak. Aşağıdaki örnek ayarlar `SqlMembershipProvider`.  
  
     Aşağıdaki örnekte, yapılandırma bölümü gösterilmektedir.  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Hizmet güvenliği kullanıcı adı/parola birleşimini kabul edecek şekilde yapılandırmak için  
  
1. Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğe, Ekle bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.  
  
2. Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) bağlamalar bölümü için. Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3. Ayarlama `mode` özniteliği `<security>` öğesine `Message`.  
  
4. Ayarlama `clientCredentialType` özniteliği <`message`> öğesine `UserName`. Bu, istemcinin kimlik bilgisi olarak bir kullanıcı adı/parola çift kullanılacak belirtir.  
  
     Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Bir hizmeti üyelik sağlayıcıyı kullanacak şekilde yapılandırmak için  
  
1. Alt öğesi olarak `<system.serviceModel>` öğe, Ekle bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi  
  
2. Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.  
  
3. Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ayarlayıp `name` özniteliği için uygun bir değer.  
  
4. Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için <`behavior`> öğesi.  
  
5. Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için `<serviceCredentials>` öğesi.  
  
6. Ayarlama `userNamePasswordValidationMode` özniteliğini `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, WCF, Windows kimlik doğrulaması yerine kullanan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.  
  
7. Ayarlama `membershipProviderName` özniteliği için (Bu konunun ilk yordamındaki sağlayıcı eklerken belirtilir) sağlayıcısının adı. Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, ASP üyelik özelliğini kullanan bir hizmet yapılandırmasını gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Üyelik ve Rol Sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
