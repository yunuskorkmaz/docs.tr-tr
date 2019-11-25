---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 804161dfe4c2b5b397505f25231b3afccb5a6476
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141709"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma
Güvenli bir oturumda durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak, oturum hizmetin geri dönüştürülmemesini sağlayabilir. Örneğin, bir durum bilgisiz SCT güvenli bir oturumda kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybedilir. Bu oturum verileri bir SCT belirteç önbelleği içerir. Bu nedenle, bir istemci hizmeti durum bilgisiz SCT ' yi bir sonraki gönderişinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür. Ancak, durum bilgisi olan bir SCT kullanılırsa, SCT ile ilişkili anahtar, SCT içinde yer alır. Anahtar SCT içinde bulunduğundan ve bu nedenle ileti içinde yer aldığı için güvenli oturum, geri dönüştürülecek hizmetten etkilenmez. Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda durum bilgisiz SCTs 'yi kullanır. Bu konuda güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında ayrıntılı bilgi verilmektedir.  
  
> [!NOTE]
> Durum bilgisi olan SCTs, <xref:System.ServiceModel.Channels.IDuplexChannel>türetilen bir sözleşmeyi içeren güvenli bir oturumda kullanılamaz.  
  
> [!NOTE]
> Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği, ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır. Hizmet, `Local Service`gibi bir kullanıcı profiline sahip olmayan bir hesap altında çalıştırıldığında bir özel durum oluşabilir.  
  
> [!NOTE]
> Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olmayan bir SCT olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanmak için  
  
- SOAP iletilerinin durum bilgisi olan bir SCT kullanan güvenli bir oturumla korunduğunu belirten özel bir bağlama oluşturun.  
  
    1. Hizmetin yapılandırma dosyasına bir [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyerek özel bir bağlama tanımlayın.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)> alt öğe [\<bağlama](../../configure-apps/file-schema/wcf/bindings.md) ekleyin.  
  
         `name` özniteliğini yapılandırma dosyası içindeki benzersiz bir ada ayarlayarak bir bağlama adı belirtin.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) alt öğesi ekleyerek bu hizmetten gelen ve giden iletiler için kimlik doğrulama modunu belirtin.  
  
         `authenticationMode` özniteliğini `SecureConversation`olarak ayarlayarak güvenli bir oturumun kullanıldığını belirtin. `requireSecurityContextCancellation` özniteliği `false`olarak ayarlanarak durum bilgisi olan SCN 'leri belirtin.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)bir [\<Securesestionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğesi ekleyerek, istemcinin nasıl doğrulandığını belirtin.  
  
         `authenticationMode` özniteliğini ayarlayarak istemcinin kimliğinin nasıl doğrulandığını belirtin.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)gibi bir kodlama öğesi ekleyerek ileti kodlamasını belirtin.  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)gibi bir taşıma öğesi ekleyerek taşımayı belirtin.  
  
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
  
 Windows kimlik doğrulaması durum bilgisi olan bir SCT ile birlikte kullanıldığında, WCF <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliğini gerçek arayanın kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar. WCF güvenliği, gelen SCT 'nin her isteği için hizmet güvenlik bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez. <xref:System.Security.Principal.WindowsIdentity> örneğinin SCT 'e serileştirilmek imkansız olduğundan, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği anonim bir kimlik döndürür.  
  
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
