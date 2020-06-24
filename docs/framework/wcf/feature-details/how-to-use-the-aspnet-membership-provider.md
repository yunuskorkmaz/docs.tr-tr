---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
description: ASP.NET üyelik sağlayıcısı 'nın, kullanıcıların bir Windows etki alanı hesabına sahip olmadan erişim için Kullanıcı adı ve parola oluşturmalarına izin veren Web sitelerini nasıl desteklediğini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246733"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma

ASP.NET üyelik sağlayıcısı, ASP.NET geliştiricilerinin kullanıcıların benzersiz Kullanıcı adı ve parola bileşimleri oluşturmalarına izin veren Web siteleri oluşturmalarına olanak tanıyan bir özelliktir. Bu tesisle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir. Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır. Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola birleşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.

Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../samples/membership-and-role-provider.md). ASP.NET rol sağlayıcısı özelliğini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmetle ASP.NET rol sağlayıcısını kullanma](how-to-use-the-aspnet-role-provider-with-a-service.md).

Üyelik özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanılmasını gerektirir. Bu özellik ayrıca, parolasını unutduğunuz tüm kullanıcılar için soru sorma yöntemleri içerir.

Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir. Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir. Verileri WCF hizmetine aktarmak için, (yapılandırmada, içinde) gibi Kullanıcı adı/parola kimlik bilgilerini destekleyen bir bağlama kullanın <xref:System.ServiceModel.WSHttpBinding> [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ve istemci kimlik bilgisi türünü olarak ayarlayın `UserName` . Hizmette, WCF güvenliği kullanıcının kimliğini Kullanıcı adı ve parolaya göre doğrular ve ayrıca ASP.NET rolü tarafından belirtilen rolü de atar.

> [!NOTE]
> WCF, veritabanını Kullanıcı adı/parola birleşimleri veya diğer kullanıcı bilgileriyle doldurmak için yöntemler sağlamaz.

### <a name="to-configure-the-membership-provider"></a>Üyelik sağlayıcısını yapılandırmak için

1. Web.config dosyasında, <`system.web`> öğesinin altında bir <`membership`> öğesi oluşturun.

2. Öğesi altında `<membership>` bir `<providers>` öğesi oluşturun.

3. <> öğesinin bir alt öğesi olarak `providers` , `<clear />` sağlayıcı koleksiyonunu temizlemek için bir öğe ekleyin.

4. Öğesi altında `<clear />` , `add` aşağıdaki öznitelikleri uygun değerlere ayarlanmış bir <> öğesi oluşturun: `name` , `type` ,, `connectionStringName` `applicationName` , `enablePasswordRetrieval` , `enablePasswordReset` , `requiresQuestionAndAnswer` , `requiresUniqueEmail` , ve `passwordFormat` . `name`Özniteliği daha sonra yapılandırma dosyasında bir değer olarak kullanılır. Aşağıdaki örnek olarak ayarlanır `SqlMembershipProvider` .

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

1. Yapılandırma dosyasında, [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altına bir [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.

2. [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)Bağlamalar bölümüne bir ekleyin. WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).

3. `mode` `<security>` Öğesinin özniteliğini olarak ayarlayın `Message` .

4. `clientCredentialType`<`message`> öğesinin özniteliğini olarak ayarlayın `UserName` . Bu, bir Kullanıcı adı/parola çiftinin istemci kimlik bilgileri olarak kullanılacağını belirtir.

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

1. Öğesi için alt öğe olarak `<system.serviceModel>` , bir öğe ekleyin [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)

2. [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md)<`behaviors`> öğesine ekleyin.

3. Bir ekleyin [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ve `name` özniteliği uygun bir değere ayarlayın.

4. [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)<`behavior`> öğesine ekleyin.

5. Öğesi öğesine ekleyin [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>` .

6. `userNamePasswordValidationMode`Özniteliğini olarak ayarlayın `MembershipProvider` .

    > [!IMPORTANT]
    > `userNamePasswordValidationMode`Değer ayarlanmamışsa, WCF ASP.NET üyelik sağlayıcısı yerine Windows kimlik doğrulamasını kullanır.

7. `membershipProviderName`Özniteliğini sağlayıcının adına ayarlayın (Bu konunun ilk yordamında sağlayıcı eklenirken belirtilir). Aşağıdaki örnek `<serviceCredentials>` Bu noktaya olan parçayı gösterir.

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

- [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Üyelik ve Rol Sağlayıcısı](../samples/membership-and-role-provider.md)
