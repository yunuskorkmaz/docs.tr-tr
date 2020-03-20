---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184790"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma

ASP.NET üyelik sağlayıcısı, ASP.NET geliştiricilerin kullanıcıların benzersiz kullanıcı adı ve parola kombinasyonları oluşturmasına olanak tanıyan Web siteleri oluşturmasına olanak tanıyan bir özelliktir. Bu tesis sayesinde, herhangi bir kullanıcı site ile bir hesap kurabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir. Bu, kullanıcıların windows etki alanında hesapları olmasını gerektiren Windows güvenliğinin tam tersidir. Bunun yerine, kimlik bilgilerini (kullanıcı adı/parola kombinasyonu) sağlayan herhangi bir kullanıcı siteyi ve hizmetlerini kullanabilir.

Örnek bir uygulama için [Üyelik ve Rol Sağlayıcısı'na](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)bakın. ASP.NET rol sağlayıcısının kullanımı hakkında bilgi için [bkz: ASP.NET Rol Sağlayıcısı'nı Hizmetle birlikte kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)

Üyelik özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanı nı kullanmayı gerektirir. Bu özellik, parolalarını unutan kullanıcılara soru sorma yöntemlerini de içerir.

Windows Communication Foundation (WCF) geliştiricileri bu özelliklerden güvenlik amacıyla yararlanabilir. Bir WCF uygulamasına entegre edildiğinde, kullanıcıların WCF istemci uygulamasına bir kullanıcı adı/parola kombinasyonu sağlaması gerekir. Verileri WCF hizmetine aktarmak için, <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada, [ \<wsHttpBinding>) ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)gibi kullanıcı adı/parola kimlik bilgilerini destekleyen bir bağlama kullanın ve istemci kimlik bilgilerini . `UserName` Hizmette, WCF güvenliği kullanıcı adını ve parolasını temel alarak kullanıcının kimliğini doğrular ve ASP.NET rolütarafından belirtilen rolü atar.

> [!NOTE]
> WCF, veritabanını kullanıcı adı/parola birleşimleri veya diğer kullanıcı bilgileriyle doldurmak için yöntemler sağlamaz.

### <a name="to-configure-the-membership-provider"></a>Üyelik sağlayıcısını yapılandırmak için

1. Web.config dosyasında, <`system.web`> öğesi altında, `membership` <bir> öğesi oluşturun.

2. Öğenin `<membership>` altında, `<providers>` bir öğe oluşturun.

3. <`providers`> öğesi için bir çocuk `<clear />` olarak, sağlayıcıların toplama floş için bir öğe ekleyin.

4. Öğe `<clear />` altında, uygun `add` değerlere ayarlanmış aşağıdaki öznitelikleri ile `name` `type`<`connectionStringName` `applicationName`> `enablePasswordRetrieval` `enablePasswordReset`öğesi `requiresQuestionAndAnswer` `requiresUniqueEmail`oluşturmak: `passwordFormat`, , , , , , , , ve . Öznitelik `name` daha sonra yapılandırma dosyasında bir değer olarak kullanılır. Aşağıdaki örnekte , `SqlMembershipProvider`''

    Aşağıdaki örnekte yapılandırma bölümü gösterilmektedir.

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Kullanıcı adı/parola birleşimini kabul etmek için hizmet güvenliğini yapılandırmak için

1. Yapılandırma dosyasında, [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi altında, [ \<bir bağlama>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.

2. Bağlayıcılar bölümüne [ \<bir wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ekleyin. WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için [bkz: Yapılandırmada Hizmet Bağlama belirtin.](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)

3. Öğenin `mode` özniteliğini `<security>` `Message`.

4. <`clientCredentialType` `message`> öğesinin özniteliğini `UserName`. Bu, istemcinin kimlik bilgisi olarak bir kullanıcı adı/parola çiftinin kullanılacağını belirtir.

    Aşağıdaki örnek, bağlama için yapılandırma kodunu gösterir.

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Üyelik sağlayıcısını kullanmak için bir hizmeti yapılandırmak için

1. Öğeye bir alt öğe [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) olarak, bir davranış>öğesi ekleyin `<system.serviceModel>`

2. <`behaviors`> öğesine [ \<bir hizmetDavranışı>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.

3. [ \<Davranış>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve `name` özniteliği uygun bir değere ayarlayın.

4. <`behavior`> öğesine [ \<>bir hizmet Kimlik Bilgileri](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.

5. Öğeye bir [ \<kullanıcıAdıKimlik>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) ekleyin. `<serviceCredentials>`

6. Özniteliği `userNamePasswordValidationMode` `MembershipProvider`' ne göre ayarlayın

    > [!IMPORTANT]
    > `userNamePasswordValidationMode` Değer ayarlı değilse, WCF ASP.NET üyelik sağlayıcısı yerine Windows kimlik doğrulamasını kullanır.

7. `membershipProviderName` Özniteliği sağlayıcının adına ayarlayın (bu konudaki ilk yordamda sağlayıcı eklerken belirtin). Aşağıdaki örnek, `<serviceCredentials>` bu noktaya parçayı gösterir.

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

Aşağıdaki kod, ASP üyelik özelliğini kullanan bir hizmetin yapılandırmasını gösterir.

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

- [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Üyelik ve Rol Sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
