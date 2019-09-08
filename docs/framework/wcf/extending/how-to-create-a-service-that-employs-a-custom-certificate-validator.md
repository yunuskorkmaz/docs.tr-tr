---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: b2407c293de7f11b90586f5a55bd759a4ea734aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795684"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma
Bu konu, Özel Sertifika doğrulayıcı 'nın nasıl uygulanacağını ve istemci ya da hizmet kimlik bilgilerinin varsayılan sertifika doğrulama mantığını özel sertifika doğrulayıcısı ile değiştirecek şekilde nasıl yapılandırılacağını gösterir.  
  
 X. 509.440 sertifikası bir istemcinin veya hizmetin kimliğini doğrulamak için kullanılıyorsa, varsayılan olarak Windows Communication Foundation (WCF) sertifikayı doğrulamak ve güvenilir olduğundan emin olmak için Windows sertifika deposu ve şifre API 'sini kullanır. Bazen yerleşik sertifika doğrulama işlevinin yeterince olmaması ve değiştirilmesi gerekir. WCF, kullanıcıların özel bir sertifika Doğrulayıcısı eklemesine izin vererek doğrulama mantığını değiştirmek için kolay bir yol sağlar. Özel bir sertifika Doğrulayıcısı belirtilmişse, WCF yerleşik sertifika doğrulama mantığını kullanmaz, ancak bunun yerine özel Doğrulayıcısı kullanır.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Özel bir sertifika Doğrulayıcısı oluşturmak için  
  
1. Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilmiş yeni bir sınıf tanımlayın.  
  
2. Soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi uygulayın. Doğrulanması gereken sertifika, yöntemine bir bağımsız değişken olarak geçirilir. Geçirilen sertifika doğrulama mantığına göre geçerli değilse, bu yöntem bir <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>oluşturur. Sertifika geçerliyse, yöntemi çağırana döner.  
  
    > [!NOTE]
    > Kimlik doğrulama hatalarını istemciye geri döndürmek için <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yönteminde bir oluşturun.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Hizmet yapılandırmasında özel bir sertifika Doğrulayıcısı belirtmek için  
  
1. [System. ServiceModel > öğesine bir > öğesi ve servicedavranışlar > ekleyin. \<](../../configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../configure-apps/file-schema/wcf/behaviors.md)  
  
2. `name` [ Bir\<davranış >](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve özniteliği uygun bir değere ayarlayın.  
  
3. Öğeye`<behavior>` bir [ \<ServiceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.  
  
4. `<serviceCredentials>` Öğeye bir `<clientCertificate>` öğe ekleyin.  
  
5. `<clientCertificate>` Öğeye bir [ \<kimlik doğrulaması >](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ekleyin.  
  
6. `customCertificateValidatorType` Özniteliği Doğrulayıcı türü olarak ayarlayın. Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.  
  
7. `certificateValidationMode` Özniteliğini olarak`Custom`ayarlayın.  
  
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
  
1. [System. ServiceModel > öğesine bir > öğesi ve servicedavranışlar > ekleyin. \<](../../configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../configure-apps/file-schema/wcf/behaviors.md)  
  
2. [ Bir\<endpointdavranışlar >](../../configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi ekleyin.  
  
3. Bir `<behavior>` öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.  
  
4. [ Bir\<ClientCredentials >](../../configure-apps/file-schema/wcf/clientcredentials.md) öğesi ekleyin.  
  
5. [ Bir\<ServiceCertificate >](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)ekleyin.  
  
6. Aşağıdaki örnekte gösterildiği gibi bir [ \<kimlik doğrulama >](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) ekleyin.  
  
7. `customCertificateValidatorType` Özniteliği Doğrulayıcı türü olarak ayarlayın.  
  
8. `certificateValidationMode` Özniteliğini olarak`Custom`ayarlayın. Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.  
  
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
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> Özellikte özel sertifika Doğrulayıcısı ' nı belirtin. <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Özelliğini kullanarak hizmet kimlik bilgilerine erişebilirsiniz.  
  
2. Ayarlama <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>İstemcideki kodu kullanarak özel bir sertifika Doğrulayıcısı belirtmek için  
  
1. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> Özelliğini kullanarak özel sertifika Doğrulayıcısı belirtin. <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Özelliğini kullanarak istemci kimlik bilgilerine erişebilirsiniz. ( [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan istemci sınıfı her zaman <xref:System.ServiceModel.ClientBase%601> sınıfından türetilir.)  
  
2. Ayarlama <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir özel sertifika doğrulayıcının ve hizmet üzerindeki kullanımının bir uygulamasını gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
