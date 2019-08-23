---
title: 'Nasıl yapılır: Güvenli Oturum Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: bdb0f89b950d086e04cbb9d6da161bd315fc64b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934375"
---
# <a name="how-to-create-a-secure-session"></a>Nasıl yapılır: Güvenli Oturum Oluşturma
BasicHttpBinding > bağlama dışında [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , Windows Communication Foundation (WCF) içindeki sistem tarafından sağlanan bağlamalar, ileti güvenliği etkinleştirildiğinde otomatik olarak güvenli oturumları kullanır.  
  
 Varsayılan olarak, güvenli oturumlar geri dönüştürülecek bir Web sunucusunu sürdürmez. Güvenli bir oturum oluşturulduğunda, istemci ve hizmet güvenli oturumla ilişkili anahtarı önbelleğe alın. İletiler alışverişi sırasında yalnızca önbelleğe alınmış anahtara yönelik bir tanımlayıcı alışverişi yapılır. Web sunucusu geri dönüştürüldüğünde, önbellek de, Web sunucusu tanımlayıcı için önbelleğe alınmış anahtarı alamadığından geri dönüştürülür. Bu durumda, istemciye geri bir özel durum oluşturulur. Durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanan güvenli oturumlar, bir Web sunucusunun geri dönüştürülmekte olmasını sağlayabilir. Güvenli bir oturumda durum bilgisi olan bir SCT kullanma hakkında daha fazla bilgi için [bkz. nasıl yapılır: Güvenli bir oturum](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)Için güvenlik bağlamı belirteci oluşturun.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Bir hizmetin, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenli oturumlar kullandığını belirtmek için  
  
- Bir hizmeti, ileti güvenliğini destekleyen sistem tarafından sağlanmış bir bağlama kullanacak şekilde yapılandırın.  
  
     BasicHttpBinding > bağlama dışında, sistem tarafından belirtilen bağlamalar ileti güvenliği kullanmak üzere yapılandırıldığında, WCF otomatik olarak güvenli oturumları kullanır. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) Aşağıdaki tabloda, ileti güvenliğini destekleyen sistem tarafından sağlanmış bağlamalar ve ileti güvenliği 'nin varsayılan güvenlik mekanizması olup olmadığı listelenmiştir.  
  
    |Sistem tarafından sağlanmış bağlama|Yapılandırma öğesi|Varsayılan olarak ileti güvenliği|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Hayır|  
  
     Aşağıdaki kod örneği, [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ileti güvenliği ve `wsHttpBinding_Calculator` güvenli oturumları kullanan adlı bir bağlama belirtmek için yapılandırmayı kullanır.  
  
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
  
     Aşağıdaki kod örneği, `secureCalculator` hizmetin güvenliğini sağlamak için [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ileti güvenliği ve güvenli oturumların kullanıldığını belirtir.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > Özniteliği`establishSecurityContext` olarak [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlanarakWSHttpBinding>için`false`güvenli oturumlar kapatılabilir. Sistem tarafından sağlanmış diğer bağlamalar için güvenli oturumlar yalnızca özel bir bağlama oluşturularak kapatılabilir.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Bir hizmetin özel bir bağlama kullanarak güvenli oturumlar kullandığını belirtmek için  
  
- SOAP iletilerinin güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
     Özel bağlama oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Sistem tarafından sağlanmış bağlamayı](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)özelleştirin.  
  
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
  
     Aşağıdaki kod örneği, güvenli bir oturumu önyüklemek için <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Bağlamalarına Genel Bakış](../../../../docs/framework/wcf/bindings-overview.md)
