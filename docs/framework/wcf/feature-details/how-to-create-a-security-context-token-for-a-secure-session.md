---
title: "Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 83e455c2377168c316bf34c25b687cde48b0fa3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma
Güvenli bir oturumda bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak oturum dönüştürülüyor hizmet dayanabilir. Örneğin, durum bilgisiz SCT güvenli bir oturumda kullanılır ve Internet Information Services (IIS) sıfırlanır sonra hizmetiyle ilişkili oturum veriler kaybolur. Bu oturum verilerini bir SCT belirteç önbelleği içerir. SCT ile ilişkili anahtar alınamadığından bu nedenle, bir istemci hizmeti durum bilgisiz SCT gönderir başlatıldığında bir hata, döndürülür. Ancak, bir durum bilgisi olan SCT kullanılıyorsa, SCT ile ilişkili anahtar SCT içinde yer alır. Anahtar SCT içinde yer alan ve bu nedenle iletinin içinde yer alan olduğundan, güvenli oturum dönüştürülüyor hizmeti tarafından etkilenmez. Varsayılan olarak, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] durum bilgisiz SCTs güvenli bir oturumda kullanır. Bu konu, güvenli bir oturumda durum bilgisi olan SCTs kullanmayı ayrıntıları verilmektedir.  
  
> [!NOTE]
>  Durum bilgisi olan SCTs türeyen bir sözleşme içerir güvenli bir oturum kullanılamaz <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Durum bilgisi olan SCTs güvenli bir oturumda kullanan uygulamalar için iş parçacığı kimliği hizmeti için bir ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır. Hizmet bir kullanıcı profili gibi sahip olmayan bir hesap altında çalıştırıldığında `Local Service`, bir özel durum oluşturulabilir.  
  
> [!NOTE]
>  Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan SCT olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Durum bilgisi olan SCTs güvenli bir oturumda kullanmak için  
  
-   SOAP iletilerine durum bilgisi olan SCT kullanan güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
    1.  Özel bağlama ekleyerek tanımlarsınız bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) dosya hizmeti için yapılandırma.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Ekleme bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) alt öğeye [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Bir bağlama ad ayarlayarak belirtin `name` yapılandırma dosyasında benzersiz bir ad özniteliği.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Bu hizmet gelen ve giden ekleyerek gönderilen iletiler için kimlik doğrulaması modunu belirtin bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) alt öğeye [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Güvenli bir oturum ayarlayarak kullanıldığını belirtmek `authenticationMode` özniteliğini `SecureConversation`. Durum bilgisi olan SCTs ayarlayarak kullanıldığını belirtin `requireSecurityContextCancellation` özniteliğini `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Güvenli oturum ekleyerek belirlenirken istemci kimlik doğrulamasının nasıl belirtin bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğeye [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         İstemci ayarlayarak kimlik doğrulamasının nasıl belirtin `authenticationMode` özniteliği.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Bir kodlama öğesi ekleyerek ileti kodlama belirtin [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Bir taşıma öğesi ekleyerek taşıma belirtin [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Aşağıdaki kod örneğinde yapılandırma iletileri güvenli bir oturumda durum bilgisi olan SCTs ile kullanabileceğiniz özel bağlama belirlemek için kullanır.  
  
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
 Aşağıdaki kod örneği kullanan özel bağlama oluşturur <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturum bootstrap için kimlik doğrulama modu.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Windows kimlik doğrulaması, bir durum bilgisi olan SCT ile birlikte kullanıldığında, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] değil doldurmak <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> gerçek çağıran özelliğiyle kimlik kullanıcının ancak bunun yerine özelliği anonim olarak ayarlar. Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik gelen SCT gelen her istek için hizmet güvenlik bağlamı içeriğini yeniden oluşturmanız gerekir, sunucu bellek güvenlik oturumu izlemek değil. Seri hale getirmek mümkün değildir çünkü <xref:System.Security.Principal.WindowsIdentity> SCT örneğine <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> anonim bir kimlik özelliği döndürür.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
