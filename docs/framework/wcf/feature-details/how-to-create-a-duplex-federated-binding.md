---
title: "Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d40d13ca861cd18cf5f2a72e94d1aca146c2c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma
<xref:System.ServiceModel.WSFederationHttpBinding>yalnızca veri birimi ve istek/yanıt iletisi exchange sözleşmeleri destekler. Çift yönlü ileti exchange sözleşmesi kullanmak için özel bağlama oluşturmanız gerekir. Aşağıdaki yordamlar bu yapılandırmada, HTTP ve TCP taşımaları için ileti mod güvenliği kullanarak ve TCP taşıma için karma mod güvenliği kullanarak nasıl gösterir. Tüm 3 bağlamaları gösteren örnek bu konunun sonunda kodudur.  
  
 Kodda bağlama de oluşturabilirsiniz. Bağlama öğeleri yığını oluşturmak için bir açıklaması için bkz: [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP ile çift yönlü federe özel bağlama oluşturmak için  
  
1.  İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının düğüm oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.  
  
2.  İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesini oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliği kümesine `FederationDuplexHttpMessageSecurityBinding`.  
  
3.  İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesini oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliği kümesine `SecureConversation`.  
  
4.  İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.  
  
5.  Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi, boş bir oluşturma [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi.  
  
6.  Aşağıdaki [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi, boş bir oluşturma [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi.  
  
7.  Aşağıdaki [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi, boş bir oluşturma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>TCP ileti güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için  
  
1.  İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının düğüm oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.   
  
2.  İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesini oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliği kümesine `FederationDuplexTcpMessageSecurityBinding`.  
  
3.  İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesini oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliği kümesine `SecureConversation`.  
  
4.  İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.  
  
5.  Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi, boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Bir çift yönlü oluşturmak için özel bağlama TCP karışık güvenlik modu ile Federasyon  
  
1.  İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının düğüm oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.   
  
2.  İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesini oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliği kümesine `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3.  İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesini oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliği kümesine `SecureConversation`.  
  
4.  İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.  
  
5.  Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi, boş bir oluşturma [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi.  
  
6.  Aşağıdaki [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi, boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.  
  
## <a name="code-sample"></a>Kod örneği  
  
#### <a name="sample-with-3-bindings"></a>Örnek 3 bağlamalarla  
  
1.  Yapılandırma dosyasına aşağıdaki kodu ekleyin.  
  
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
