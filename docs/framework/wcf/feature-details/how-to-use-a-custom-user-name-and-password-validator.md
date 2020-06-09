---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601185"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma

Varsayılan olarak, kimlik doğrulaması için bir Kullanıcı adı ve parola kullanıldığında, Windows Communication Foundation (WCF) Kullanıcı adı ve parolayı doğrulamak için Windows 'u kullanır. Ancak, WCF, Özel Kullanıcı adı ve parola kimlik doğrulama şemaları için, *doğrulayıcılar*olarak da bilinir. Özel bir Kullanıcı adı ve parola doğrulayıcısı eklemek için, öğesinden türeten bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve ardından yapılandırın.

Örnek bir uygulama için bkz. [Kullanıcı adı parola doğrulayıcısı](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmak için

1. Öğesinden türetilen bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Yöntemi geçersiz kılarak özel kimlik doğrulama düzenini uygulayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .

    Aşağıdaki örnekte, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamındaki yöntemi geçersiz kılan kodu kullanmayın. Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.

    Kimlik doğrulama hatalarını istemciye geri döndürmek için yönteminde bir oluşturun <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Bir hizmeti özel Kullanıcı adı ve parola doğrulayıcısı kullanacak şekilde yapılandırmak için

1. HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenliği üzerinde ileti güvenliği kullanan bir bağlama yapılandırın.

    İleti güvenliği kullanırken, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ileti güvenliğini ve kimlik bilgisi türünü destekleyen bir veya gibi sistem tarafından belirtilen bağlamalardan birini ekleyin `UserName` .

    HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) http (s) ve kimlik doğrulama düzeni kullanan veya, a ya da bir öğesini ekleyin `Basic` .

    > [!NOTE]
    > .NET Framework 3,5 veya sonraki sürümleri kullanırken ileti ve aktarım güvenliği ile özel bir Kullanıcı adı ve parola doğrulayıcısı kullanabilirsiniz. WinFX ile özel bir Kullanıcı adı ve parola doğrulayıcısı yalnızca ileti güvenliği ile birlikte kullanılabilir.

    > [!TIP]
    > Bu bağlamda kullanma hakkında daha fazla bilgi için \<netTcpBinding> bkz [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) ..

    1. Yapılandırma dosyasında, [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altına bir [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.

    2. [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) Bağlamalar bölümüne or öğesi ekleyin. WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).

    3. `mode` [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) Veya özniteliğini [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` , `Transport` veya `TransportWithMessageCredential` olarak ayarlayın.

    4. `clientCredentialType`Veya özniteliğini ayarlayın [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .

        İleti güvenliği kullanırken `clientCredentialType` , öğesinin özniteliğini [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) olarak ayarlayın `UserName` .

        HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, `clientCredentialType` [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya özniteliğini olarak ayarlayın [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) `Basic` .

        > [!NOTE]
        > Bir WCF hizmeti, aktarım düzeyi güvenlik kullanılarak Internet Information Services (IIS) içinde barındırılıyorsa ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği olarak ayarlandığında <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , özel kimlik doğrulama düzeni Windows kimlik doğrulamasının bir alt kümesini kullanır. Bunun nedeni, bu senaryoda IIS, özel kimlik doğrulayıcı çağırma WCF öncesinde Windows kimlik doğrulaması gerçekleştirir.

    WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).

    Aşağıdaki örnekte, bağlama için yapılandırma kodu gösterilmektedir:

    ```xml
    <system.serviceModel>
      <bindings>
      <wsHttpBinding>
          <binding name="Binding1">
            <security mode="Message">
              <message clientCredentialType="UserName" />
            </security>
          </binding>
        </wsHttpBinding>
      </bindings>
    </system.serviceModel>
    ```

2. Gelen güvenlik belirteçleri için Kullanıcı adı ve parola çiftlerini doğrulamak üzere özel bir Kullanıcı adı ve parola doğrulayıcısı kullanıldığını belirten bir davranış yapılandırın <xref:System.IdentityModel.Tokens.UserNameSecurityToken> .

    1. Öğesi için alt öğe olarak [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) bir [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.

    2. Öğesi öğesine ekleyin [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) .

    3. Bir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.

    4. Öğesi öğesine ekleyin [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    5. [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md)Öğesine öğesine ekleyin [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .

    6. Öğesini `userNamePasswordValidationMode` olarak ayarlayın `Custom` .

        > [!IMPORTANT]
        > `userNamePasswordValidationMode`Değer ayarlanmamışsa, WCF özel Kullanıcı adı ve parola doğrulayıcısı yerine Windows kimlik doğrulamasını kullanır.

    7. Öğesini `customUserNamePasswordValidatorType` Özel Kullanıcı adınızı ve parola doğrulayıcılarınızı temsil eden türe ayarlayın.

    Aşağıdaki örnek `<serviceCredentials>` Bu noktaya olan parçayı gösterir:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmayı gösterir. Bir üretim ortamındaki yöntemi geçersiz kılan kodu kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> . Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](how-to-use-the-aspnet-membership-provider.md)
- [Kimlik Doğrulaması](authentication-in-wcf.md)
