---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 49271e087ad63020e695f3bd46d7f8c47adf2130
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662498"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma
Varsayılan olarak, Windows Communication Foundation (WCF) Windows kullanıcı adı ve parola kullanılabilir olduğunda kimlik doğrulaması için kullanıcı adını ve parolasını doğrulamak için kullanır. Ancak, WCF özel kullanıcı adı ve parola kimlik doğrulaması düzeni için olarak da bilinen tanır *doğrulayıcıları*. Özel kullanıcı adı ve parola Doğrulayıcı eklemek için türetilen bir sınıf oluşturma <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve ardından yapılandırın.  
  
 Örnek bir uygulama için bkz: [kullanıcı Adıparola Doğrulayıcı](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Özel kullanıcı adı ve parola Doğrulayıcı oluşturma  
  
1. Türetilen bir sınıf oluşturmanız <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. Özel kimlik doğrulama şeması geçersiz kılarak uygulamak <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.  
  
     Kodu geçersiz kılan aşağıdaki örnekte kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi. Kullanıcı adı ve parola çiftleri veritabanından alınırken gerektirebilir, özel kullanıcı adı ve parola doğrulama şeması ile değiştirin.  
  
     Kimlik doğrulama hataları istemciye geri dönmek için throw bir <xref:System.ServiceModel.FaultException> içinde <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Özel kullanıcı adı ve parola Doğrulayıcı kullanmak için bir hizmeti yapılandırmak için  
  
1. HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenlik ileti güvenliği kullanan bir bağlama yapılandırın.  
  
     İleti güveliği kullanarak, bir sistem tarafından sağlanan bağlamalar gibi ekleyin. bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), veya bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ileti güvenliği destekler ve `UserName` kimlik bilgisi türü.  
  
     HTTP (S) üzerinden aktarım düzeyi güvenlik kullanılırken ekleyin ya da [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) veya [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) HTTP (S) kullanan ve `Basic` kimlik doğrulama düzeni.  
  
    > [!NOTE]
    >  Zaman [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] veya daha sonra kullanıldığında özel bir kullanıcı adı ve parola Doğrulayıcı ileti ve aktarım güvenliği ile kullanabilirsiniz. İle [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], özel bir kullanıcı adı ve parola Doğrulayıcı ile ileti güvenliği yalnızca kullanılabilir.  
  
    > [!TIP]
    >  Kullanma hakkında daha fazla bilgi için \<netTcpBinding > Bu bağlam içinde görebilir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1. Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğe, Ekle bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.  
  
    2. Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlamalar bölümü öğesi. Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3. Ayarlama `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) veya [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message`, `Transport`, veya `TransportWithMessageCredential`.  
  
    4. Ayarlama `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         İleti güveliği kullanarak, ayarlama `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) için `UserName`.  
  
         HTTP (S) üzerinden aktarım düzeyi güvenlik kullanılırken ayarlamak `clientCredentialType` özniteliği [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) için `Basic`.  
  
        > [!NOTE]
        >  Bir WCF hizmeti Internet Information Services (aktarım düzeyi güvenlik kullanarak IIS içinde) barındırılan ne zaman ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, Windows kimlik doğrulama kümesini özel kimlik doğrulama şeması kullanır. Bu senaryoda, IIS WCF özel authenticator çağırmadan önce Windows kimlik doğrulaması gerçekleştirdiğinden olmasıdır.  
  
     Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.  
  
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
  
2. Özel kullanıcı adı ve parola Doğrulayıcı gelen kullanıcı adı ve parola çiftlerini doğrulamak için kullanıldığını belirten bir davranış yapılandırma <xref:System.IdentityModel.Tokens.UserNameSecurityToken> güvenlik belirteçleri.  
  
    1. Alt öğesi olarak [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğe, Ekle bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
    2. Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
    3. Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ve kümesi `name` özniteliği için uygun bir değer.  
  
    4. Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.  
  
    5. Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6. Ayarlama `userNamePasswordValidationMode` için `Custom`.  
  
        > [!IMPORTANT]
        >  Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, WCF, Windows kimlik doğrulaması yerine özel bir kullanıcı adı ve parola Doğrulayıcı kullanır.  
  
    7. Ayarlama `customUserNamePasswordValidatorType` için özel kullanıcı adı ve parola Doğrulayıcı temsil eden tür.  
  
     Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, özel kullanıcı adı ve parola Doğrulayıcı oluşturma işlemini gösterir. Geçersiz kılmalar kod kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi. Kullanıcı adı ve parola çiftleri veritabanından alınırken gerektirebilir, özel kullanıcı adı ve parola doğrulama şeması ile değiştirin.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
