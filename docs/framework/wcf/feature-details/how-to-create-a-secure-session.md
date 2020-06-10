---
title: 'Nasıl yapılır: Güvenli Oturum Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593418"
---
# <a name="how-to-create-a-secure-session"></a>Nasıl yapılır: Güvenli Oturum Oluşturma
[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)Bağlama dışında, Windows Communication Foundation (WCF) içindeki sistem tarafından sağlanan bağlamalar, ileti güvenliği etkinleştirildiğinde otomatik olarak güvenli oturumları kullanır.  
  
 Varsayılan olarak, güvenli oturumlar geri dönüştürülecek bir Web sunucusunu sürdürmez. Güvenli bir oturum oluşturulduğunda, istemci ve hizmet güvenli oturumla ilişkili anahtarı önbelleğe alın. İletiler alışverişi sırasında yalnızca önbelleğe alınmış anahtara yönelik bir tanımlayıcı alışverişi yapılır. Web sunucusu geri dönüştürüldüğünde, önbellek de, Web sunucusu tanımlayıcı için önbelleğe alınmış anahtarı alamadığından geri dönüştürülür. Bu durumda, istemciye geri bir özel durum oluşturulur. Durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanan güvenli oturumlar, bir Web sunucusunun geri dönüştürülmekte olmasını sağlayabilir. Güvenli bir oturumda durum bilgisi olan bir SCT kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Bir hizmetin, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenli oturumlar kullandığını belirtmek için  
  
- Bir hizmeti, ileti güvenliğini destekleyen sistem tarafından sağlanmış bir bağlama kullanacak şekilde yapılandırın.  
  
     [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)Bağlama dışında, sistem tarafından belirtilen bağlamalar ileti güvenliği kullanmak üzere yapılandırıldığında, WCF otomatik olarak güvenli oturumları kullanır. Aşağıdaki tabloda, ileti güvenliğini destekleyen sistem tarafından sağlanmış bağlamalar ve ileti güvenliği 'nin varsayılan güvenlik mekanizması olup olmadığı listelenmiştir.  
  
    |Sistem tarafından sağlanmış bağlama|Yapılandırma öğesi|Varsayılan olarak ileti güvenliği|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|Yes|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Yes|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Yes|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|Hayır|  
  
     Aşağıdaki kod örneği `wsHttpBinding_Calculator` [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ,, ileti güvenliği ve güvenli oturumları kullanan adlı bir bağlama belirtmek için yapılandırmayı kullanır.  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     Aşağıdaki kod örneği [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , hizmeti güvenli hale getirmek için ileti güvenliği ve güvenli oturumların kullanıldığını belirtir `secureCalculator` .  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > İçin güvenli oturumlar, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) `establishSecurityContext` özniteliği olarak ayarlanarak kapatılabilir `false` . Sistem tarafından sağlanmış diğer bağlamalar için güvenli oturumlar yalnızca özel bir bağlama oluşturularak kapatılabilir.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Bir hizmetin özel bir bağlama kullanarak güvenli oturumlar kullandığını belirtmek için  
  
- SOAP iletilerinin güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
     Özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: sistem tarafından sağlanmış bağlamayı özelleştirme](../extending/how-to-customize-a-system-provided-binding.md).  
  
     Aşağıdaki kod örneği, güvenli bir oturum kullanan iletilerin özel bir bağlamasını belirtmek için yapılandırmayı kullanır.  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     Aşağıdaki kod örneği, <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturumu önyüklemek için kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Bağlamaları Genel Bakış](../bindings-overview.md)
