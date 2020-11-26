---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 31918ca2d96b63911130d22476a6e5a6d48999ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249247"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma

Bu konu, Özel Sertifika doğrulayıcı 'nın nasıl uygulanacağını ve istemci ya da hizmet kimlik bilgilerinin varsayılan sertifika doğrulama mantığını özel sertifika doğrulayıcısı ile değiştirecek şekilde nasıl yapılandırılacağını gösterir.  
  
 X. 509.440 sertifikası bir istemcinin veya hizmetin kimliğini doğrulamak için kullanılıyorsa, varsayılan olarak Windows Communication Foundation (WCF) sertifikayı doğrulamak ve güvenilir olduğundan emin olmak için Windows sertifika deposu ve şifre API 'sini kullanır. Bazen yerleşik sertifika doğrulama işlevinin yeterince olmaması ve değiştirilmesi gerekir. WCF, kullanıcıların özel bir sertifika Doğrulayıcısı eklemesine izin vererek doğrulama mantığını değiştirmek için kolay bir yol sağlar. Özel bir sertifika Doğrulayıcısı belirtilmişse, WCF yerleşik sertifika doğrulama mantığını kullanmaz, ancak bunun yerine özel Doğrulayıcısı kullanır.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Özel bir sertifika Doğrulayıcısı oluşturmak için  
  
1. Öğesinden türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.X509CertificateValidator> .  
  
2. Soyut yöntemi uygulayın <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> . Doğrulanması gereken sertifika, yöntemine bir bağımsız değişken olarak geçirilir. Geçirilen sertifika doğrulama mantığına göre geçerli değilse, bu yöntem bir oluşturur <xref:System.IdentityModel.Tokens.SecurityTokenValidationException> . Sertifika geçerliyse, yöntemi çağırana döner.  
  
    > [!NOTE]
    > Kimlik doğrulama hatalarını istemciye geri döndürmek için yönteminde bir oluşturun <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Hizmet yapılandırmasında özel bir sertifika Doğrulayıcısı belirtmek için  
  
1. Öğesine bir [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve öğesi ekleyin [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
2. Bir ekleyin [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ve `name` özniteliği uygun bir değere ayarlayın.  
  
3. Öğesi öğesine ekleyin [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>` .  
  
4. Öğeye bir `<clientCertificate>` öğe ekleyin `<serviceCredentials>` .  
  
5. [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>` Öğesini öğesine ekleyin.  
  
6. `customCertificateValidatorType`Özniteliği Doğrulayıcı türü olarak ayarlayın. Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.  
  
7. `certificateValidationMode`Özniteliğini olarak ayarlayın `Custom` .  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>İstemcideki yapılandırmayı kullanarak özel bir sertifika Doğrulayıcısı belirtmek için  
  
1. Öğesine bir [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve öğesi ekleyin [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
2. Bir [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) öğe ekleyin.  
  
3. Bir `<behavior>` öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.  
  
4. Bir [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) öğe ekleyin.  
  
5. Bir ekleyin [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
6. [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)Aşağıdaki örnekte gösterildiği gibi ekleyin.  
  
7. `customCertificateValidatorType`Özniteliği Doğrulayıcı türü olarak ayarlayın.  
  
8. `certificateValidationMode`Özniteliğini olarak ayarlayın `Custom` . Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Hizmette kod kullanarak özel bir sertifika Doğrulayıcısı belirtmek için  
  
1. Özellikte özel sertifika Doğrulayıcısı ' nı belirtin <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> . Özelliğini kullanarak hizmet kimlik bilgilerine erişebilirsiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> .  
  
2. <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A>Özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> .  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>İstemcideki kodu kullanarak özel bir sertifika Doğrulayıcısı belirtmek için  
  
1. Özelliğini kullanarak özel sertifika Doğrulayıcısı belirtin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> . Özelliğini kullanarak istemci kimlik bilgilerine erişebilirsiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> . ( [ServiceModel meta veri yardımcı programı](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan istemci sınıfı (Svcutil.exe) her zaman sınıfından türetilir <xref:System.ServiceModel.ClientBase%601> .)  
  
2. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A>Özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> .  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  

 Aşağıdaki örnek, bir özel sertifika doğrulayıcının ve hizmet üzerindeki kullanımının bir uygulamasını gösterir.  
  
### <a name="code"></a>Kod  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
