---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185571"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma
Bu konu, özel sertifika doğrulayıcısının nasıl uygulanacağını ve varsayılan sertifika doğrulama mantığını özel sertifika doğrulayıcısıyla değiştirmek için istemci veya hizmet kimlik bilgilerini nasıl yapılandıracağını gösterir.  
  
 X.509 sertifikası bir istemcinin veya hizmetin kimliğini doğrulamak için kullanılırsa, Windows Communication Foundation (WCF) varsayılan olarak sertifikayı doğrulamak ve güvenilir olduğundan emin olmak için Windows sertifika deposunu ve Crypto API'yi kullanır. Bazen yerleşik sertifika doğrulama işlevi yeterli değildir ve değiştirilmesi gerekir. WCF, kullanıcıların özel sertifika doğrulayıcısı eklemesine izin vererek doğrulama mantığını değiştirmenin kolay bir yolunu sağlar. Özel sertifika doğrulayıcısı belirtilmişse, WCF yerleşik sertifika doğrulama mantığını kullanmaz, ancak bunun yerine özel doğrulayıcıya dayanır.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Özel sertifika doğrulayıcısı oluşturmak için  
  
1. Türetilen yeni bir <xref:System.IdentityModel.Selectors.X509CertificateValidator>sınıf tanımlayın.  
  
2. Soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi uygulayın. Doğrulanması gereken sertifika yönteme bağımsız değişken olarak geçirilir. Geçirilen sertifika doğrulama mantığına göre geçerli değilse, bu yöntem <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>bir . Sertifika geçerliyse, yöntem arayana döner.  
  
    > [!NOTE]
    > Kimlik doğrulama hatalarını istemciye geri <xref:System.ServiceModel.FaultException> döndürmek <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> için yönteme bir a atın.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Hizmet yapılandırmasında özel sertifika doğrulayıcısı belirtmek için  
  
1. Bir [ \<davranış>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.  
  
2. [ \<Davranış>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve `name` özniteliği uygun bir değere ayarlayın.  
  
3. Öğeye [ \<>bir hizmet Kimlik Bilgileri](../../configure-apps/file-schema/wcf/servicecredentials.md) ekleyin. `<behavior>`  
  
4. `<serviceCredentials>` Öğeye bir `<clientCertificate>` öğe ekleyin.  
  
5. Öğeye [ \<kimlik doğrulama>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ekleyin. `<clientCertificate>`  
  
6. `customCertificateValidatorType` Özniteliği doğrulayıcı türüne ayarlayın. Aşağıdaki örnek, ad alanı ve türün adı özniteliğini ayarlar.  
  
7. Özniteliği `certificateValidationMode` `Custom`' ne göre ayarlayın  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>İstemci üzerinde yapılandırma yı kullanarak özel sertifika doğrulayıcıbelirtmek için  
  
1. Bir [ \<davranış>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.  
  
2. [ \<Bir bitiş noktasıDavranışı>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi ekleyin.  
  
3. Bir `<behavior>` öğe ekleyin `name` ve özniteliği uygun bir değere ayarlayın.  
  
4. [ \<Bir istemci kimlik bilgileri>](../../configure-apps/file-schema/wcf/clientcredentials.md) öğesi ekleyin.  
  
5. [ \<ServiceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)ekle.  
  
6. Aşağıdaki örnekte gösterildiği gibi [ \<kimlik doğrulama>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) ekleyin.  
  
7. `customCertificateValidatorType` Özniteliği doğrulayıcı türüne ayarlayın.  
  
8. Özniteliği `certificateValidationMode` `Custom`' ne göre ayarlayın Aşağıdaki örnek, ad alanı ve türün adı özniteliğini ayarlar.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Hizmette kodu kullanarak özel sertifika doğrulayıcı belirtmek için  
  
1. Özellikteki özel sertifika doğrulayıcısını belirtin. <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> Özelliği kullanarak hizmet kimlik <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> bilgilerine erişebilirsiniz.  
  
2. Özelliği <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> ' <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>ye ayarlayın.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>İstemci üzerinde kod kullanarak özel bir sertifika doğrulayıcı belirtmek için  
  
1. Özelliği kullanarak özel sertifika doğrulayıcısını belirtin. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> Özelliği kullanarak istemci kimlik <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> bilgilerine erişebilirsiniz. [(ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan istemci <xref:System.ServiceModel.ClientBase%601> sınıfı her zaman sınıftan türetilmiştir.)  
  
2. Özelliği <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> ' <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>ye ayarlayın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, özel sertifika doğrulayıcısının uygulanmasını ve hizmetüzerindeki kullanımını gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
