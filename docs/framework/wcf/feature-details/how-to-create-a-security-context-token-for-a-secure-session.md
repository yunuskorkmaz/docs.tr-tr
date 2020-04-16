---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 4e91580035d4de23ae90cd0d59a08f321ae70a1c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464142"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma
Güvenli bir oturumda durumsal bir güvenlik bağlamı belirteci (SCT) kullanarak, oturum geri dönüştürülen hizmete dayanabilir. Örneğin, güvenli bir oturumda durum bilgisi olmayan bir SCT kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybolur. Bu oturum verileri bir SCT belirteç önbelleği içerir. Bu nedenle, bir istemci hizmeti bir sonraki kez durumsuz bir SCT gönderdiğinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür. Ancak, durum lu bir ÖST kullanılırsa, ÖSK ile ilişkili anahtar ÖSK içinde bulunur. Anahtar ÖST içinde ve böylece ileti içinde bulunduğundan, güvenli oturum geri dönüştürülen hizmetten etkilenmez. Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda devletsiz SCT'leri kullanır. Bu konu, güvenli bir oturumda durum lu SCT'lerin nasıl kullanılacağını ayrıntılarıyla anlatır.  
  
> [!NOTE]
> Stateful SCT'ler, <xref:System.ServiceModel.Channels.IDuplexChannel>'den türeyen bir sözleşme içeren güvenli bir oturumda kullanılamaz.  
  
> [!NOTE]
> Güvenli bir oturumda durum daki SCT'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği ilişkili bir kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır. Hizmet, kullanıcı profili olmayan bir hesap altında `Local Service`çalıştırıldığında, örneğin , bir özel durum atılabilir.  
  
> [!NOTE]
> Windows XP'de kimliğe bürünme gerektiğinde, devlete uygun bir SCT olmadan güvenli bir oturum kullanın. Stateful SCTs kimliğe bürünme <xref:System.InvalidOperationException> ile kullanıldığında, bir atılır. Daha fazla bilgi için [desteklenmeyen senaryolar'a](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)bakın.  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Güvenli bir oturumda durum lu SCT'leri kullanmak için  
  
- SOAP iletilerinin özel bir ÖTV kullanan güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
    1. Hizmetin yapılandırma dosyasına [ \<özel](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlayıcı>ekleyerek özel bir bağlama tanımlayın.  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. Bağlayıcı [ \<>](../../configure-apps/file-schema/wcf/bindings.md) alt öğesi [özelBağlayıcı>. \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         Yapılandırma dosyasındaki `name` benzersiz bir ada özniteliği ayarlayarak bağlayıcı bir ad belirtin.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. ÖzelBağlayıcı>'ne bir [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) alt öğesi ekleyerek bu hizmete ve bu hizmetten gönderilen iletilerin kimlik doğrulama modunu belirtin. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         Özniteliği ' ne `authenticationMode` `SecureConversation`ayarlayarak güvenli bir oturumun kullanıldığını belirtin Stateful SCT'lerin `requireSecurityContextCancellation` özniteliği ni atlayarak `false`kullanıldığını belirtin.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. Güvenli oturum güvenlik>güvenli bir [ \<ConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğe ekleyerek kurulurken istemcinin nasıl doğrulanmış olduğunu belirtin. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
         Öznitelik ayarlayarak istemcinin nasıl `authenticationMode` doğrulanmış olduğunu belirtin.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. [ \<TextMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)gibi bir kodlama öğesi ekleyerek ileti kodlamasını belirtin.  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)gibi bir aktarım öğesi ekleyerek aktarım'ı belirtin.  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Aşağıdaki kod örneği, iletilerin güvenli bir oturumda durum daki SCT'lerle kullanabileceği özel bir bağlama belirtmek için yapılandırmayı kullanır.  
  
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
 Aşağıdaki kod örneği, güvenli bir oturumu <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> önyükleme için kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Windows kimlik doğrulaması durum salkıcısı ile birlikte kullanıldığında, WCF özelliği gerçek arayanın <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar. WCF security'nin gelen SCT'den gelen her istek için hizmet güvenliği bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez. <xref:System.Security.Principal.WindowsIdentity> Örneği SCT'ye seri hale getirmek mümkün <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> olmadığından, özellik anonim bir kimlik döndürür.  
  
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

- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
