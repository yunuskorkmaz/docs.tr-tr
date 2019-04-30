---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 510faa0b1d791b1d164c55e9fa32daafa559d56c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696216"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma
<xref:System.ServiceModel.WSFederationHttpBinding> yalnızca veri birimi ve istek/yanıt iletisi exchange sözleşmeleri destekler. Çift yönlü ileti exchange anlaşması kullanmak için özel bir bağlama oluşturmanız gerekir. Aşağıdaki yordamlar yapılandırmasında, HTTP ve TCP taşımalar için ileti modu güvenliği ve karma mod güvenliği için TCP taşıması kullanarak bunun nasıl yapılacağını gösterir. Tüm 3 bağlamaları gösteren örnek kodlara, bu konunun sonunda ' dir.  
  
 Ayrıca, kod içinde bağlama oluşturabilirsiniz. Oluşturmak için bağlama öğeleri yığın açıklaması için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP ile özel çift yönlü federe bağlama oluşturma  
  
1. İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası düğümü oluşturmak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.  
  
2. İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliğini `FederationDuplexHttpMessageSecurityBinding`.  
  
3. İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliğini `SecureConversation`.  
  
4. İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.  
  
5. Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi boş bir oluşturma [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi.  
  
6. Aşağıdaki [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi boş bir oluşturma [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi.  
  
7. Aşağıdaki [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi boş bir oluşturma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>TCP ileti güvenlik modunu ile özel çift yönlü federe bağlama oluşturma  
  
1. İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası düğümü oluşturmak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.   
  
2. İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliğini `FederationDuplexTcpMessageSecurityBinding`.  
  
3. İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliğini `SecureConversation`.  
  
4. İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.  
  
5. Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Bir çift yönlü oluşturmak için özel bir bağlama TCP karma güvenlik modu ile Federasyon  
  
1. İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası düğümü oluşturmak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.   
  
2. İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliğini `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3. İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliğini `SecureConversation`.  
  
4. İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.  
  
5. Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi boş bir oluşturma [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi.  
  
6. Aşağıdaki [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.  
  
## <a name="code-sample"></a>Kod örneği  
  
#### <a name="sample-with-3-bindings"></a>Örnek 3 bağlamaları ile  
  
1. Yapılandırma dosyanıza aşağıdaki kodu ekleyin.  
  
## <a name="example"></a>Örnek  
  
```xml  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
```
