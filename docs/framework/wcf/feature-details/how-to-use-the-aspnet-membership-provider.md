---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: c2567b6abd42ae725b4786eb111e411f7328154e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939795"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma
ASP.NET üyelik sağlayıcısı, ASP.NET geliştiricilerinin kullanıcıların benzersiz Kullanıcı adı ve parola bileşimleri oluşturmalarına izin veren Web siteleri oluşturmalarına olanak tanıyan bir özelliktir. Bu tesisle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir. Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır. Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola bileşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.  
  
 Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). ASP.NET rol sağlayıcısı özelliğini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)birlikte kullanın.  
  
 Üyelik özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanılmasını gerektirir. Bu özellik ayrıca, parolasını unutduğunuz tüm kullanıcılar için soru sorma yöntemleri içerir.  
  
 Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir. Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir. Verileri WCF hizmetine aktarmak için, <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada `UserName` [ \<, WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) gibi Kullanıcı adı/parola kimlik bilgilerini destekleyen bir bağlama kullanın ve istemci kimlik bilgileri türünü olarak ayarlayın. Hizmette, WCF güvenliği kullanıcının kimliğini Kullanıcı adı ve parolaya göre doğrular ve ayrıca ASP.NET rolü tarafından belirtilen rolü de atar.  
  
> [!NOTE]
> WCF, veritabanını Kullanıcı adı/parola birleşimleri veya diğer kullanıcı bilgileriyle doldurmak için yöntemler sağlamaz.  
  
### <a name="to-configure-the-membership-provider"></a>Üyelik sağlayıcısını yapılandırmak için  
  
1. Web. config dosyasında, <`system.web`> öğesi altında, bir <`membership`> öğesi oluşturun.  
  
2. Öğesi altında bir `<providers>` öğesi oluşturun. `<membership>`  
  
3. <`providers`> Öğesinin bir alt öğesi olarak, sağlayıcı koleksiyonunu temizlemek `<clear />` için bir öğe ekleyin.  
  
4. `connectionStringName` `name` `enablePasswordRetrieval` `requiresQuestionAndAnswer` Öğesialtında`applicationName`, aşağıdaki öznitelikleri uygun değerlere`add`ayarlanmış bir < > öğesi oluşturun:, `type`,,,, `enablePasswordReset`, `<clear />` , `requiresUniqueEmail`ve .`passwordFormat` `name` Özniteliği daha sonra yapılandırma dosyasında bir değer olarak kullanılır. Aşağıdaki örnek olarak `SqlMembershipProvider`ayarlanır.  
  
     Aşağıdaki örnek yapılandırma bölümünü gösterir.  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Hizmet güvenliğini Kullanıcı adı/parola birleşimini kabul edecek şekilde yapılandırmak için  
  
1. Yapılandırma dosyasında, [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altında bir [ \<Bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.  
  
2. Bağlamalar bölümüne bir [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ekleyin. WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin.  
  
3. Ayarlama `mode` özniteliği `<security>` öğesine `Message`.  
  
4. `UserName`< `clientCredentialType` >Öğesininözniteliğiniolarakayarlayın`message`. Bu, bir Kullanıcı adı/parola çiftinin istemci kimlik bilgileri olarak kullanılacağını belirtir.  
  
     Aşağıdaki örnek, bağlamanın yapılandırma kodunu gösterir.  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Üyelik sağlayıcısını kullanmak üzere bir hizmeti yapılandırmak için  
  
1. `<system.serviceModel>` Öğesi için alt öğe olarak, [ \<> bir davranış](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) ekleyin  
  
2. <`behaviors`> Öğesine bir [ \<servicedavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.  
  
3. `name` [ Bir\<davranış >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve özniteliği uygun bir değere ayarlayın.  
  
4. <`behavior`> Öğesine bir [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.  
  
5. `<serviceCredentials>` Öğesine bir [ \<UserNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) ekleyin.  
  
6. `userNamePasswordValidationMode` Özniteliğini olarak`MembershipProvider`ayarlayın.  
  
    > [!IMPORTANT]
    >  `userNamePasswordValidationMode` Değer ayarlanmamışsa, WCF ASP.NET üyelik sağlayıcısı yerine Windows kimlik doğrulamasını kullanır.  
  
7. `membershipProviderName` Özniteliğini sağlayıcının adına ayarlayın (Bu konunun ilk yordamında sağlayıcı eklenirken belirtilir). Aşağıdaki örnek bu noktaya olan `<serviceCredentials>` parçayı gösterir.  
  
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
 Aşağıdaki kod, ASP üyeliği özelliğini kullanan bir hizmetin yapılandırmasını gösterir.  
  
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
