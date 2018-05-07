---
title: 'Nasıl yapılır: Güvenli Oturum Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ce351a87e70b09a2f68654af817e28fa3145d79d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-secure-session"></a>Nasıl yapılır: Güvenli Oturum Oluşturma
Dışında [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlama, sistem tarafından sağlanan bağlamalar Windows Communication Foundation (WCF) otomatik olarak ileti güvenliği etkinleştirildiğinde güvenli oturumlar kullanın.  
  
 Varsayılan olarak, güvenli oturumlar geri dönüştürüldüğünde bir Web sunucusu varlığını sürdürmesini değil. Güvenli bir oturum oluşturulduğunda, istemci ve hizmet güvenli oturumla ilişkili anahtar önbelleğe. Değiştirilen mesajları gibi yalnızca bir tanımlayıcı önbelleğe alınan anahtarına değiştirilir. Web sunucusu geri dönüştürüldüğünde ise sağlayacak şekilde Web sunucusu tanımlayıcısı için önbelleğe alınan anahtar alınamıyor önbellek Ayrıca, dönüştürülmeden. Bu durumda, bir özel durum istemciye geri atılır. Bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanan güvenli oturumlar dönüştürüldüğü bir Web sunucusu varlığını sürdürmesini. Durum bilgisi olan SCT güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Sistem tarafından sağlanan bağlamalar birini kullanarak bir hizmeti güvenli oturumlar kullandığını belirlemek için  
  
-   İleti güvenliği destekleyen sistem tarafından sağlanan bir bağlamayı kullanmak amacıyla hizmeti yapılandırın.  
  
     Dışında [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlama, sistem tarafından sağlanan bağlamalar zaman ileti güvenliği, WCF otomatik olarak kullanmak üzere yapılandırılmış güvenli oturumlar kullanır. İleti güvenliği ve ileti güvenliği varsayılan güvenlik mekanizması olup destek sistem tarafından sağlanan bağlamaları aşağıdaki tabloda listelenmektedir.  
  
    |Sistem tarafından sağlanan bağlama|Yapılandırma öğesi|Varsayılan ileti güvenliği|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Hayır|  
  
     Adlı bir bağlama belirtmek için aşağıdaki kod örneğinde yapılandırmasını kullanan `wsHttpBinding_Calculator` kullanan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ileti güvenlik ve güvenli oturumlar.  
  
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
  
     Aşağıdaki kod örneğinde belirtir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ileti güvenlik ve güvenli oturumlar güvenliğini sağlamak için kullanılan `secureCalculator` hizmet.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Güvenli oturumlar açılabilir için [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlayarak `establishSecurityContext` özniteliğini `false`. Özel bağlama oluşturarak diğer sistem tarafından sağlanan bağlamaları için yalnızca güvenli oturumlar kapatılabilir.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Özel bağlama kullanarak bir hizmeti güvenli oturumlar kullandığını belirlemek için  
  
-   SOAP iletilerine güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
     Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: System-Provided bir bağlamayı özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     Aşağıdaki kod örneği, bir özel bağlama güvenli oturum kullanarak bu iletileri belirtmek için yapılandırma kullanır.  
  
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
  
     Aşağıdaki kod örneği kullanan özel bağlama oluşturur <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturum bootstrap için kimlik doğrulama modu.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Bağlamalarına Genel Bakış](../../../../docs/framework/wcf/bindings-overview.md)
