---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
author: BrucePerlerMS
ms.openlocfilehash: 85954dd89bdb576b68d234a364a406a6e0d2145b
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261335"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma
Güvenli bir oturumda bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak oturum dönüştürüldüğü hizmet dayanabilir. Örneği için bir durum bilgisi olmayan SCT güvenli bir oturumda kullanılır ve Internet Information Services (IIS) sıfırlama, ardından hizmeti ile ilişkili oturum veriler kaybolur. Bu oturum verileri SCT belirteç önbelleği içerir. SCT ile ilişkili anahtarı alınamıyor çünkü bu nedenle, sonraki açışınızda bir istemci hizmeti bir durum bilgisi olmayan SCT gönderir. hata, döndürülür. Ancak, bir durum bilgisi olan SCT kullanılıyorsa, SCT ile ilişkili anahtar SCT içinde yer alır. Anahtar SCT içinde yer alan ve bu nedenle ileti içinde yer alan olduğundan, güvenli oturum dönüştürüldüğü hizmeti tarafından etkilenmez. Varsayılan olarak, Windows Communication Foundation (WCF), durum bilgisiz SCTs güvenli bir oturumda kullanır. Bu konu, güvenli bir oturumda durum bilgisi olan SCTs kullanma işlemi açıklanmaktadır.  
  
> [!NOTE]
>  Durum bilgisi olan SCTs türetildiği bir sözleşme içeren güvenli bir oturum kullanılamaz <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Durum bilgisi olan SCTs güvenli bir oturumda kullanan uygulamalar için hizmeti için iş parçacığı kimliği bir ilişkili kullanıcı profili olan bir kullanıcı hesabı olmalıdır. Hizmet bir kullanıcı profili gibi sahip olmayan bir hesap altında çalıştırın, `Local Service`, bir özel durum.  
  
> [!NOTE]
>  Kimliğe bürünme Windows XP'de gerektiğinde, durum bilgisi olan SCT olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. Daha fazla bilgi için [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Durum bilgisi olan SCTs güvenli bir oturumda kullanmak için  
  
-   SOAP iletilerini durum bilgisi olan SCT kullanan güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
    1.  Özel bir bağlama ekleyerek tanımlamak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) hizmet yapılandırma dosyası.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Ekleme bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) alt öğeye [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Bağlama adına ayarlayarak belirtin `name` yapılandırma dosyası içinde benzersiz bir ad özniteliği.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Kimlik doğrulama modu için ve bu hizmetten ekleyerek gönderilen iletiler için belirtin bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) alt öğeye [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Güvenli bir oturum ayarlayarak kullanıldığını belirtmek `authenticationMode` özniteliğini `SecureConversation`. Durum bilgisi olan SCTs ayarlayarak kullanıldığını belirtmek `requireSecurityContextCancellation` özniteliğini `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  İstemci ekleyerek güvenli oturum belirlenirken nasıl doğrulandığını belirtin bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğeye [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         İstemci ayarı nasıl doğrulandığını belirtin `authenticationMode` özniteliği.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Bir kodlama öğesi ekleyerek ileti kodlama belirtin [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Taşıma bir transport öğesi ekleyerek belirtin [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Aşağıdaki kod örneği yapılandırma iletileri güvenli bir oturumda ile durum bilgisi olan SCTs kullanabileceğiniz özel bir bağlama belirtmek için kullanır.  
  
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
 Aşağıdaki kod örneği kullanan özel bir bağlama oluşturur <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturum bootstrap için kimlik doğrulama modu.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Windows kimlik doğrulaması, bir durum bilgisi olan SCT ile birlikte kullanıldığında, WCF değil doldurmak <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> gerçek arayan özelliğiyle kimlik kullanıcının ancak bunun yerine özellik anonim olarak ayarlar. WCF güvenlik içeriği gelen SCT her istekte hizmet güvenlik bağlamı yeniden oluşturmanız gerekir, çünkü sunucunun bellek güvenlik oturumu izler mi değil. Seri hale getirmek mümkün değildir çünkü <xref:System.Security.Principal.WindowsIdentity> SCT örneğine <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> anonim bir kimlik özelliği döndürür.  
  
 Aşağıdaki yapılandırma, bu davranışı sergiler.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
