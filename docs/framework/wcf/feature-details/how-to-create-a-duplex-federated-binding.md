---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141722"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma

<xref:System.ServiceModel.WSFederationHttpBinding> yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler. Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir. Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir. Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.

Ayrıca, koddaki bağlamayı da oluşturabilirsiniz. Oluşturulacak bağlama öğeleri yığınının bir açıklaması için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP ile çift yönlü federe özel bağlama oluşturmak için

1. Yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) düğümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.

2. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesinin içinde `name` özniteliği `FederationDuplexHttpMessageSecurityBinding`olarak ayarlanmış bir [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun.

3. [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin içinde `authenticationMode` özniteliği `SecureConversation`olarak ayarlanmış bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun.

4. [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesinin içinde `authenticationMode` özniteliği `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`olarak ayarlanmış bir [\<securebir Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi oluşturun.

5. [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini izleyerek boş bir [\<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi oluşturun.

6. [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesini izleyerek boş bir [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi oluşturun.

7. [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesini izleyerek boş bir [\<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi oluşturun.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için

1. Yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) düğümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.

2. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesinin içinde `name` özniteliği `FederationDuplexTcpMessageSecurityBinding`olarak ayarlanmış bir [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun.

3. [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin içinde `authenticationMode` özniteliği `SecureConversation`olarak ayarlanmış bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun.

4. [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesinin içinde `authenticationMode` özniteliği `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`olarak ayarlanmış bir [\<securebir Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi oluşturun.

5. [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini izleyerek boş bir [\<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için

1. Yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) düğümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.

2. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesinin içinde `name` özniteliği `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`olarak ayarlanmış bir [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun.

3. [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin içinde `authenticationMode` özniteliği `SecureConversation`olarak ayarlanmış bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun.

4. [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesinin içinde `authenticationMode` özniteliği `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`olarak ayarlanmış bir [\<securebir Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi oluşturun.

5. [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini izleyerek boş bir [\<sslstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi oluşturun.

6. [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesini izleyerek boş bir [\<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun.

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
