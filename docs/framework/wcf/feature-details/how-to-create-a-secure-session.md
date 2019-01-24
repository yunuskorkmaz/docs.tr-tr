---
title: 'Nasıl yapılır: Güvenli oturum oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: c2e2b34c1d1589f26f3aea80384b5a96f1c64fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544724"
---
# <a name="how-to-create-a-secure-session"></a>Nasıl yapılır: Güvenli oturum oluşturma
Dışında [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlama, sistem tarafından sağlanan bağlamalar Windows Communication Foundation (WCF) otomatik olarak ileti güvenliği etkinleştirildiğinde güvenli oturumlar kullanın.  
  
 Varsayılan olarak, güvenli oturumlar dönüştürülmeden bir Web sunucusu sürdürmez. Güvenli bir oturum kurulduktan sonra istemci ve hizmet güvenli bir oturum ile ilişkili anahtar önbelleğe alın. Önbelleğe alınan anahtarı için bir tanımlayıcı mesajları olarak değiştirilir. Web sunucusu dönüştürülmeden, Web sunucusunda önbelleğe alınan anahtar tanımlayıcısı alınamıyor, önbellek Ayrıca, dönüştürülmeden. Bu durumda, bir özel durum geri istemcinin durum oluşturulur. Bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanan güvenli oturumlar dönüştürüldüğü bir Web sunucusu hayatta kalamaz. Durum bilgisi olan SCT güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Sistem tarafından sağlanan bağlamalar birini kullanarak bir hizmeti güvenli oturumlar kullandığını belirtmek için  
  
-   İleti güvenliği destekleyen sistem tarafından sağlanan bir bağlamayı kullanmak için bir hizmet yapılandırın.  
  
     Dışında [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlama, sistem tarafından sağlanan bağlamalar ileti güvenliği, WCF otomatik olarak kullanmak için yapılandırılmış zaman güvenli oturumlar kullanır. İleti güvenliği ve ileti güvenliği varsayılan güvenlik mekanizması olup destekleyen sistem tarafından sağlanan bağlamaları aşağıdaki tabloda listelenmektedir.  
  
    |Sistem tarafından sağlanan bir bağlamayı|Yapılandırma öğesi|Varsayılan ileti güvenliği|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Evet|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Hayır|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Hayır|  
  
     Aşağıdaki kod örneği, adında bir bağlaması belirtmek için yapılandırma kullanır. `wsHttpBinding_Calculator` kullanan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ileti güvenlik ve güvenli oturumlar.  
  
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
  
     Aşağıdaki kod örneği belirtir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ileti güvenlik ve güvenli oturumlar güvenliğini sağlamak için kullanılan `secureCalculator` hizmeti.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Güvenli oturumlar kapatılabilir için [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlayarak `establishSecurityContext` özniteliğini `false`. Özel bağlama oluşturarak diğer sistem tarafından sağlanan bağlamalar için yalnızca güvenli oturumlar kapatılabilir.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Özel bağlama kullanarak bir hizmeti güvenli oturumlar kullandığını belirtmek için  
  
-   SOAP iletilerini güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.  
  
     Özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
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
  
     Aşağıdaki kod örneği kullanan özel bir bağlama oluşturur <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturum bootstrap için kimlik doğrulama modu.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Bağlamalarına Genel Bakış](../../../../docs/framework/wcf/bindings-overview.md)
