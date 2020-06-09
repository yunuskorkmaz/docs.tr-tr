---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 36cf5ce1aa6e0eef80123ac7008294062d7faf82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598911"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma
Güvenli bir oturumda durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak, oturum hizmetin geri dönüştürülmemesini sağlayabilir. Örneğin, bir durum bilgisiz SCT güvenli bir oturumda kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybedilir. Bu oturum verileri bir SCT belirteç önbelleği içerir. Bu nedenle, bir istemci hizmeti durum bilgisiz SCT ' yi bir sonraki gönderişinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür. Ancak, durum bilgisi olan bir SCT kullanılırsa, SCT ile ilişkili anahtar, SCT içinde yer alır. Anahtar SCT içinde bulunduğundan ve bu nedenle ileti içinde yer aldığı için güvenli oturum, geri dönüştürülecek hizmetten etkilenmez. Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda durum bilgisiz SCTs 'yi kullanır. Bu konuda güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında ayrıntılı bilgi verilmektedir.  
  
> [!NOTE]
> Durum bilgisi olan SCN 'ler, öğesinden türetilen bir sözleşmeyi içeren güvenli bir oturumda kullanılamaz <xref:System.ServiceModel.Channels.IDuplexChannel> .  
  
> [!NOTE]
> Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği, ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır. Hizmet, gibi bir kullanıcı profiline sahip olmayan bir hesap altında çalıştırıldığında `Local Service` bir özel durum oluşabilir.  
  
> [!NOTE]
> Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olmayan bir SCT olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir oluşturulur <xref:System.InvalidOperationException> . Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanmak için  
  
- SOAP iletilerinin durum bilgisi olan bir SCT kullanan güvenli bir oturumla korunduğunu belirten özel bir bağlama oluşturun.  
  
    1. Hizmet için yapılandırma dosyasına bir ekleyerek özel bir bağlama tanımlayın [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. Öğesine bir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) alt öğesi ekleyin [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
         `name`Özniteliği yapılandırma dosyası içindeki benzersiz bir ada ayarlayarak bir bağlama adı belirtin.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. Öğesine bir alt öğe ekleyerek bu hizmetten gönderilen ve giden iletiler için kimlik doğrulama modunu belirtin [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
         Özniteliğini olarak ayarlayarak güvenli bir oturumun kullanıldığını belirtin `authenticationMode` `SecureConversation` . Özniteliği olarak ayarlanarak durum bilgisi olan SCN 'leri belirtin `requireSecurityContextCancellation` `false` .  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. ' Ye bir alt öğesi eklenerek, güvenli oturum oluşturulduğunda istemcinin nasıl doğrulandığını belirtin [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .  
  
         Özniteliğini ayarlayarak istemcinin kimliğinin nasıl doğrulandığını belirtin `authenticationMode` .  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Bir kodlama öğesi ekleyerek ileti kodlamasını belirtin (örneğin,) [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Taşıma öğesi ekleyerek taşımayı belirtin [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .  
  
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
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturumu önyüklemek için kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Windows kimlik doğrulaması durum bilgisi olan bir SCT ile birlikte kullanıldığında, WCF, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği gerçek arayanın kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar. WCF güvenliği, gelen SCT 'nin her isteği için hizmet güvenlik bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez. Örneği SCT 'e seri hale getirmek imkansız olduğundan <xref:System.Security.Principal.WindowsIdentity> , <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> Özelliği anonim bir kimlik döndürür.  
  
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

- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
