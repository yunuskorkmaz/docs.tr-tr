---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598976"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma

<xref:System.ServiceModel.WSFederationHttpBinding>yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler. Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir. Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir. Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.

Ayrıca, koddaki bağlamayı da oluşturabilirsiniz. Oluşturulacak bağlama öğeleri yığınının bir açıklaması için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP ile çift yönlü federe özel bağlama oluşturmak için

1. [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.

2. Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexHttpMessageSecurityBinding` .

3. Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .

4. Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .

5. Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) öğe oluşturun.

6. Öğesini izleyerek [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) boş bir [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) öğe oluşturun.

7. Öğesini izleyerek [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) boş bir [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) öğe oluşturun.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için

1. [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.

2. Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexTcpMessageSecurityBinding` .

3. Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .

4. Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .

5. Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) öğe oluşturun.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için

1. [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.

2. Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .

3. Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .

4. Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .

5. Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) öğe oluşturun.

6. Öğesini izleyerek [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) boş bir [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) öğe oluşturun.

## <a name="code-sample"></a>Kod örneği

### <a name="sample-with-3-bindings"></a>3 bağlamalarla örnek

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
