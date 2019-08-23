---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: e6c41ed32d63932bc1fac72bc6e727eb82806617
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966079"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma
Güvenli bir oturumda durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak, oturum hizmetin geri dönüştürülmemesini sağlayabilir. Örneğin, bir durum bilgisiz SCT güvenli bir oturumda kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybedilir. Bu oturum verileri bir SCT belirteç önbelleği içerir. Bu nedenle, bir istemci hizmeti durum bilgisiz SCT ' yi bir sonraki gönderişinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür. Ancak, durum bilgisi olan bir SCT kullanılırsa, SCT ile ilişkili anahtar, SCT içinde yer alır. Anahtar SCT içinde bulunduğundan ve bu nedenle ileti içinde yer aldığı için güvenli oturum, geri dönüştürülecek hizmetten etkilenmez. Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda durum bilgisiz SCTs 'yi kullanır. Bu konuda güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında ayrıntılı bilgi verilmektedir.  
  
> [!NOTE]
> Durum bilgisi olan SCN 'ler, öğesinden <xref:System.ServiceModel.Channels.IDuplexChannel>türetilen bir sözleşmeyi içeren güvenli bir oturumda kullanılamaz.  
  
> [!NOTE]
> Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği, ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır. Hizmet, gibi bir kullanıcı profiline `Local Service`sahip olmayan bir hesap altında çalıştırıldığında bir özel durum oluşabilir.  
  
> [!NOTE]
> Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olmayan bir SCT olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanmak için  
  
- SOAP iletilerinin durum bilgisi olan bir SCT kullanan güvenli bir oturumla korunduğunu belirten özel bir bağlama oluşturun.  
  
    1. Hizmetin yapılandırma dosyasına bir [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyerek özel bir bağlama tanımlayın.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. CustomBinding > bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) [alt öğesi ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         `name` Özniteliği yapılandırma dosyası içindeki benzersiz bir ada ayarlayarak bir bağlama adı belirtin.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. CustomBinding > bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [alt öğesi ekleyerek bu hizmetten gelen ve giden iletiler için kimlik doğrulama modunu belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         `authenticationMode` Özniteliğini olarak`SecureConversation`ayarlayarak güvenli bir oturumun kullanıldığını belirtin. `requireSecurityContextCancellation` Özniteliği olarak`false`ayarlanarak durum bilgisi olan SCN 'leri belirtin.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. Güvenlik > bir [ \<securesestionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) [alt öğesi eklenerek, istemcinin nasıl doğrulandığını belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
         `authenticationMode` Özniteliğini ayarlayarak istemcinin kimliğinin nasıl doğrulandığını belirtin.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. TextMessageEncoding > gibi bir kodlama öğesi [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)ekleyerek ileti kodlamasını belirtin.  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. [ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)gibi bir taşıma öğesi ekleyerek taşımayı belirtin.  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Aşağıdaki kod örneği, iletilerin, güvenli bir oturumda durum bilgisi olan SCN 'ler ile kullanabileceği özel bir bağlama belirtmek için yapılandırmayı kullanır.  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, güvenli bir oturumu önyüklemek için <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Windows kimlik doğrulaması durum bilgisi olan bir SCT ile birlikte kullanıldığında, WCF, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği gerçek arayanın kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar. WCF güvenliği, gelen SCT 'nin her isteği için hizmet güvenlik bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez. <xref:System.Security.Principal.WindowsIdentity> Örneği SCT 'e seri hale getirmek imkansız olduğundan <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> , özelliği anonim bir kimlik döndürür.  
  
 Aşağıdaki yapılandırma bu davranışı sergiler.  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
