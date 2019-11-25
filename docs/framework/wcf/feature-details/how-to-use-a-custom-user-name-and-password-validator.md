---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 3d01a29671f42e80fdb7ca45223007aa60273ba9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283254"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma

Varsayılan olarak, kimlik doğrulaması için bir Kullanıcı adı ve parola kullanıldığında, Windows Communication Foundation (WCF) Kullanıcı adı ve parolayı doğrulamak için Windows 'u kullanır. Ancak, WCF, Özel Kullanıcı adı ve parola kimlik doğrulama şemaları için, *doğrulayıcılar*olarak da bilinir. Özel bir Kullanıcı adı ve parola doğrulayıcısı eklemek için, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> türeten bir sınıf oluşturun ve ardından yapılandırın.

Örnek bir uygulama için bkz. [Kullanıcı adı parola doğrulayıcısı](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmak için

1. <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türeten bir sınıf oluşturun.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemini geçersiz kılarak özel kimlik doğrulama düzenini uygulayın.

    Aşağıdaki örnekte, bir üretim ortamındaki <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemini geçersiz kılan kodu kullanmayın. Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.

    Kimlik doğrulama hatalarını istemciye geri döndürmek için <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yönteminde bir <xref:System.ServiceModel.FaultException> oluşturun.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Bir hizmeti özel Kullanıcı adı ve parola doğrulayıcısı kullanacak şekilde yapılandırmak için

1. HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenliği üzerinde ileti güvenliği kullanan bir bağlama yapılandırın.

    İleti güvenliği kullanırken, [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)gibi sistem tarafından belirtilen bağlamalardan birini veya ileti güvenliğini ve `UserName` kimlik bilgisi türünü destekleyen bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyin.

    HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [\<wshttpbinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) veya [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), [\<NETTCPBINDING >](../../configure-apps/file-schema/wcf/nettcpbinding.md) veya http (S) ve\<kimlik doğrulama düzenini kullanan bir [> CustomBinding `Basic`](../../configure-apps/file-schema/wcf/custombinding.md) ekleyin.

    > [!NOTE]
    > .NET Framework 3,5 veya sonraki sürümleri kullanırken ileti ve aktarım güvenliği ile özel bir Kullanıcı adı ve parola doğrulayıcısı kullanabilirsiniz. WinFX ile özel bir Kullanıcı adı ve parola doğrulayıcısı yalnızca ileti güvenliği ile birlikte kullanılabilir.

    > [!TIP]
    > Bu bağlamda \<netTcpBinding > kullanma hakkında daha fazla bilgi için bkz [\<güvenlik >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).

    1. Yapılandırma dosyasında, [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altında, bir [\<bağlamaları >](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.

    2. Bağlamalar bölümüne [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) veya [\<BasicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md) öğesi ekleyin. WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).

    3. [\<güvenlik >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` özniteliğini veya [\<güvenlik >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message`, `Transport`veya `TransportWithMessageCredential`olarak ayarlayın.

    4. [\<iletisinin >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) veya [\<taşıma >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)`clientCredentialType` özniteliğini ayarlayın.

        İleti güvenliği kullanırken, [\<iletisinin >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) `clientCredentialType` özniteliğini `UserName`olarak ayarlayın.

        HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [\<taşıma >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [\<taşıma >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) `clientCredentialType` özniteliğini `Basic`olarak ayarlayın.

        > [!NOTE]
        > Bir WCF hizmeti, aktarım düzeyi güvenlik kullanarak Internet Information Services (IIS) içinde barındırılıyorsa ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>olarak ayarlandığında, özel kimlik doğrulama düzeni Windows kimlik doğrulamasının bir alt kümesini kullanır. Bunun nedeni, bu senaryoda IIS, özel kimlik doğrulayıcı çağırma WCF öncesinde Windows kimlik doğrulaması gerçekleştirir.

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

2. Gelen <xref:System.IdentityModel.Tokens.UserNameSecurityToken> güvenlik belirteçleri için Kullanıcı adı ve parola çiftlerini doğrulamak üzere özel bir Kullanıcı adı ve parola doğrulayıcısı kullanıldığını belirten bir davranış yapılandırın.

    1. [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin bir alt öğesi olarak [\<davranışlar >](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.

    2. [\<davranışlar >](../../configure-apps/file-schema/wcf/behaviors.md) öğesine [>\<servicedavranışlar](../../configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.

    3. [\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.

    4. [\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesine [\<ServiceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.

    5. [\<serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<UserNameAuthentication >](../../configure-apps/file-schema/wcf/usernameauthentication.md) ekleyin.

    6. `userNamePasswordValidationMode` `Custom`olarak ayarlayın.

        > [!IMPORTANT]
        > `userNamePasswordValidationMode` değeri ayarlanmamışsa, WCF özel Kullanıcı adı ve parola doğrulayıcısı yerine Windows kimlik doğrulamasını kullanır.

    7. `customUserNamePasswordValidatorType`, Özel Kullanıcı adınızı ve parola doğrulayıcılarınızı temsil eden türe ayarlayın.

    Aşağıdaki örnek, `<serviceCredentials>` parçasını bu noktaya gösterir:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmayı gösterir. Bir üretim ortamındaki <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi geçersiz kılan kodu kullanmayın. Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](how-to-use-the-aspnet-membership-provider.md)
- [Kimlik doğrulaması](authentication-in-wcf.md)
