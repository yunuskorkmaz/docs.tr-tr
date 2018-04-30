---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ea4f4d7021f02d239b9e2e93a85b5baaf5a0317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma
Bir kullanıcı adı ve parola kullanıldığında kimlik doğrulaması için varsayılan olarak, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Windows kullanıcı adı ve parolayı doğrulamak için kullanır. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel kullanıcı adı ve parola kimlik doğrulaması düzeni için olarak da bilinen sağlar *doğrulayıcıları*. Özel kullanıcı adı ve parola Doğrulayıcı içerecek şekilde türeyen bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve ardından yapılandırın.  
  
 Örnek bir uygulama için bkz: [kullanıcı Adıparola Doğrulayıcı](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Özel kullanıcı adı ve parola Doğrulayıcı oluşturmak için  
  
1.  Türeyen bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  Özel kimlik doğrulama şeması geçersiz kılarak uygulamak <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.  
  
     Kodu geçersiz kılar aşağıdaki örnekte kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi. Kullanıcı adı ve parola çiftleri veritabanından alma de girer, özel kullanıcı adı ve parola doğrulama düzeni, kodu değiştirin.  
  
     Kimlik doğrulama hataları istemciye geri dönmek için throw bir <xref:System.ServiceModel.FaultException> içinde <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Özel kullanıcı adı ve parola Doğrulayıcı kullanmak için bir hizmeti yapılandırmak için  
  
1.  İleti güvenliği HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyinde güvenlik kullanan bir bağlama yapılandırın.  
  
     İleti güvenliği kullanırken, sistem tarafından sağlanan bağlamalar birini gibi ekleyin. bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), veya bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ileti güvenliği destekler ve `UserName` kimlik bilgisi türü.  
  
     HTTP (S) üzerinden aktarım düzeyinde güvenlik kullanırken, ekleyip ya da [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) veya [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) HTTP (S) kullanan ve `Basic` kimlik doğrulama düzeni.  
  
    > [!NOTE]
    >  Zaman [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] veya daha sonraki bir sürümü kullanıldığında, özel bir kullanıcı adı ve parola Doğrulayıcı ileti ve taşıma güvenliği ile kullanabilirsiniz. İle [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], özel bir kullanıcı adı ve parola Doğrulayıcı ile ileti güvenliği yalnızca kullanılabilir.  
  
    > [!TIP]
    >  Kullanma hakkında daha fazla bilgi için \<netTcpBinding > Bu bağlamda bkz [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1.  Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleme bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.  
  
    2.  Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlamaları bölümüne öğesi. Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğesi, bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3.  Ayarlama `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) veya [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message`, `Transport`, `or``TransportWithMessageCredential`.  
  
    4.  Ayarlama `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         İleti güvenliği kullanırken ayarlayın `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) için `UserName`.  
  
         HTTP (S) üzerinden aktarım düzeyinde güvenlik kullanırken, ayarlayın `clientCredentialType` özniteliği [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) için `Basic`.  
  
        > [!NOTE]
        >  Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Internet Information Services (aktarım düzeyi güvenlik kullanarak IIS içinde) barındırılan hizmetin ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, özel kimlik doğrulama şeması bir alt kümesini Windows kimlik doğrulaması kullanır. Bu senaryoda, IIS Windows kimlik doğrulaması öncesinde gerçekleştirdiğinden olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel Doğrulayıcı çağırma.  
  
     Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğesi, bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
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
  
2.  Özel kullanıcı adı ve parola Doğrulayıcı gelen için kullanıcı adı ve parola çiftlerini doğrulamak için kullanıldığını belirtir davranışını yapılandırma <xref:System.IdentityModel.Tokens.UserNameSecurityToken> güvenlik belirteçleri.  
  
    1.  Alt öğesi olarak [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
    2.  Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
    3.  Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ve kümesi `name` öznitelik için uygun bir değer.  
  
    4.  Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.  
  
    5.  Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6.  Ayarlama `userNamePasswordValidationMode` için `Custom`.  
  
        > [!IMPORTANT]
        >  Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yerine özel bir kullanıcı adı ve parola Doğrulayıcı Windows kimlik doğrulaması kullanır.  
  
    7.  Ayarlama `customUserNamePasswordValidatorType` için özel bir kullanıcı adı ve parola Doğrulayıcı temsil eden tür.  
  
     Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl özel bir kullanıcı adı ve parola Doğrulayıcı oluşturulacağını gösterir. Geçersiz kılmaları kod kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi. Kullanıcı adı ve parola çiftleri veritabanından alma de girer, özel kullanıcı adı ve parola doğrulama düzeni, kodu değiştirin.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
