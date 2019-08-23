---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 57bd650caef831f3ee886c0422e13cc4149d3416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968802"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma
Varsayılan olarak, kimlik doğrulaması için bir Kullanıcı adı ve parola kullanıldığında, Windows Communication Foundation (WCF) Kullanıcı adı ve parolayı doğrulamak için Windows 'u kullanır. Ancak, WCF, Özel Kullanıcı adı ve parola kimlik doğrulama şemaları için, *doğrulayıcılar*olarak da bilinir. Özel bir Kullanıcı adı ve parola doğrulayıcısı eklemek için, öğesinden <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> türeten bir sınıf oluşturun ve ardından yapılandırın.  
  
 Örnek bir uygulama için bkz. [Kullanıcı adı parola doğrulayıcısı](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmak için  
  
1. Öğesinden <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilen bir sınıf oluşturun.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> Yöntemi geçersiz kılarak özel kimlik doğrulama düzenini uygulayın.  
  
     Aşağıdaki örnekte, bir üretim ortamındaki <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi geçersiz kılan kodu kullanmayın. Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.  
  
     Kimlik doğrulama hatalarını istemciye geri döndürmek için <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yönteminde bir oluşturun.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Bir hizmeti özel Kullanıcı adı ve parola doğrulayıcısı kullanacak şekilde yapılandırmak için  
  
1. HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenliği üzerinde ileti güvenliği kullanan bir bağlama yapılandırın.  
  
     İleti güvenliği kullanırken, bir [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)gibi sistem tarafından belirtilen bağlamalardan birini veya ileti güvenliğini ve `UserName` kimlik bilgisi türünü destekleyen bir [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyin.  
  
     HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<NetTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ya da bir [ \<CustomBinding ekleyin > ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)bu, `Basic` http (S) ve kimlik doğrulama düzeni kullanır.  
  
    > [!NOTE]
    > [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Veya sonraki bir sürümü kullanıldığında ileti ve aktarım güvenliği ile özel bir Kullanıcı adı ve parola doğrulayıcısı kullanabilirsiniz. WinFX ile özel bir Kullanıcı adı ve parola doğrulayıcısı yalnızca ileti güvenliği ile birlikte kullanılabilir.  
  
    > [!TIP]
    >  Bu bağlamda NetTcpBinding \<> kullanma hakkında daha fazla bilgi için bkz [ \<. Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1. Yapılandırma dosyasında, [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altında bir [ \<Bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.  
  
    2. Bağlamalar bölümüne bir [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi ekleyin. WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin.  
  
    3. `mode` Güvenlik>`Transport`veya Güvenlik>özniteliğini`TransportWithMessageCredential`,veyaolarak ayarlayın. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message`  
  
    4. İleti > veya `clientCredentialType` [Aktarım >özniteliğiniayarlayın\<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md). [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)  
  
         İleti güvenliği kullanırken `clientCredentialType` [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) özniteliğini olarak `UserName`ayarlayın.  
  
         HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, `clientCredentialType` [ \<taşıma >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) özniteliğini olarak `Basic`ayarlayın.  
  
        > [!NOTE]
        >  Bir WCF hizmeti, aktarım düzeyi güvenlik kullanılarak Internet Information Services (IIS) içinde barındırılıyorsa ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği olarak <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>ayarlandığında, özel kimlik doğrulama düzeni Windows kimlik doğrulamasının bir alt kümesini kullanır. Bunun nedeni, bu senaryoda IIS, özel kimlik doğrulayıcı çağırma WCF öncesinde Windows kimlik doğrulaması gerçekleştirir.  
  
     WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin.  
  
     Aşağıdaki örnek, bağlamanın yapılandırma kodunu gösterir.  
  
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
  
    1. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi için alt öğe olarak bir davranışlar > öğesi ekleyin.  
  
    2. Davranışlar > öğesine bir [ \<servicedavranışlar](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [> ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
    3. [ Bir\<davranış >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) `name` öğesi ekleyin ve özniteliği uygun bir değere ayarlayın.  
  
    4. Davranış > öğesine bir [ \<ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) [> ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
    5. ServiceCredentials > bir [ \<UserNameAuthentication>ekleyin](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) . [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
    6. `userNamePasswordValidationMode` Öğesini olarak`Custom`ayarlayın.  
  
        > [!IMPORTANT]
        >  `userNamePasswordValidationMode` Değer ayarlanmamışsa, WCF özel Kullanıcı adı ve parola doğrulayıcısı yerine Windows kimlik doğrulamasını kullanır.  
  
    7. `customUserNamePasswordValidatorType` Öğesini özel kullanıcı adınızı ve parola doğrulayıcılarınızı temsil eden türe ayarlayın.  
  
     Aşağıdaki örnek bu noktaya olan `<serviceCredentials>` parçayı gösterir.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmayı gösterir. Bir üretim ortamındaki <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi geçersiz kılan kodu kullanmayın. Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
