---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: b7e8e4a750aadd8a84a57cdf22c01f6b91e6256c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296556"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma
Bu konuda, özel bir sertifika Doğrulayıcı uygulama ve varsayılan sertifika doğrulama mantığı ile özel bir sertifika Doğrulayıcı değiştirmek için istemci veya hizmet kimlik bilgilerinin nasıl yapılandırılacağı gösterilmektedir.  
  
 X.509 Sertifika bir istemci veya hizmetin kimliğini doğrulamak için kullanılıyorsa, Windows Communication Foundation (WCF) varsayılan olarak Windows sertifika deposu ve şifreleme API'si günlük kaydını güvenilir olduğundan emin olun ve sertifikayı doğrulamak için kullanır. Bazen yerleşik sertifika doğrulama işlevselliği yeterli değildir ve değiştirilmesi gerekir. WCF özel bir sertifika Doğrulayıcı ekleme olanak tanıyarak Doğrulama mantığı değiştirmek için kolay bir yol sağlar. Özel bir sertifika Doğrulayıcı belirtilirse, WCF yerleşik Sertifika Doğrulama mantığı kullanmaz, ancak bunun yerine özel doğrulayıcısındaki kullanır.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Özel bir sertifika Doğrulayıcı oluşturma  
  
1. Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2. Özet uygulama <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi. Doğrulanması gereken sertifikayı yönteme bağımsız değişken olarak geçirilir. Geçirilen sertifika doğrulama mantığı göre geçerli değilse, bu yöntemin oluşturduğu bir <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Sertifika geçerliyse, metodu çağırana döner.  
  
    > [!NOTE]
    >  Kimlik doğrulama hataları istemciye geri dönmek için throw bir <xref:System.ServiceModel.FaultException> içinde <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Hizmet yapılandırmasında özel bir sertifika Doğrulayıcı belirtmek için  
  
1. Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.  
  
2. Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ayarlayıp `name` özniteliği için uygun bir değer.  
  
3. Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için `<behavior>` öğesi.  
  
4. Ekleme bir `<clientCertificate>` öğesine `<serviceCredentials>` öğesi.  
  
5. Ekleme bir [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) için `<clientCertificate>` öğesi.  
  
6. Ayarlama `customCertificateValidatorType` öznitelik için Doğrulayıcı türü. Aşağıdaki örnekte, öznitelik ad alanı ve tür adını ayarlar.  
  
7. Ayarlama `certificateValidationMode` özniteliğini `Custom`.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>İstemcide yapılandırmayı kullanarak özel bir sertifika Doğrulayıcı belirtmek için  
  
1. Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.  
  
2. Ekleme bir [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi.  
  
3. Ekleme bir `<behavior>` öğesi ve kümesi `name` özniteliği için uygun bir değer.  
  
4. Ekleme bir [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi.  
  
5. Ekleme bir [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6. Ekleme bir [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) üzerinde aşağıdaki örnekte gösterildiği gibi.  
  
7. Ayarlama `customCertificateValidatorType` öznitelik için Doğrulayıcı türü.  
  
8. Ayarlama `certificateValidationMode` özniteliğini `Custom`. Aşağıdaki örnekte, öznitelik ad alanı ve tür adını ayarlar.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Hizmette kod kullanarak özel bir sertifika Doğrulayıcı belirtmek için  
  
1. Özel bir sertifika Doğrulayıcı belirtin <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> özelliği. Hizmet kimlik bilgilerini kullanarak erişebileceğiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği.  
  
2. Ayarlama <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>İstemcide kod kullanarak özel bir sertifika Doğrulayıcı belirtmek için  
  
1. Kullanarak özel bir sertifika Doğrulayıcı belirtin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> özelliği. İstemci kimlik bilgileri ile erişebileceğiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği. (Tarafından oluşturulan istemci sınıfını [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) her zaman türetilen <xref:System.ServiceModel.ClientBase%601> sınıfı.)  
  
2. Ayarlama <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, hizmette özel bir sertifika Doğrulayıcı ve bunun kullanımını uygulanışı gösterilmektedir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
