---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972055"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma

<xref:System.ServiceModel.WSFederationHttpBinding>yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler. Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir. Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir. Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.

Ayrıca, koddaki bağlamayı da oluşturabilirsiniz. Oluşturulacak bağlama öğeleri yığınının bir açıklaması için bkz [. nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)kullanarak özel bir bağlama oluşturun.

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP ile çift yönlü federe özel bağlama oluşturmak için

1. Yapılandırma dosyasının [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlamalar > düğümünde bir CustomBinding > öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. CustomBinding > öğesinin içinde, `name` özniteliği olarak ayarlanmış`FederationDuplexHttpMessageSecurityBinding`bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. Bağlama > öğesinin içinde, `authenticationMode` özniteliği olarak ayarlanmış`SecureConversation`bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun. [ \<](../../../../docs/framework/misc/binding.md)

4. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` `IssuedTokenForCertificate` [ Güvenlik>öğesiiçinde,veyaolarakayarlananözniteliğiilebirsecurebir\<Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesioluşturun`IssuedTokenForSslNegotiated`.

5. Güvenlik > öğesini izleyerek boş [ \<bir CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

6. CompositeDuplex > öğeden sonra boş [ \<bir oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)

7. OneWay > öğesini izleyerek boş [ \<bir HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için

1. Yapılandırma dosyasının [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlamalar > düğümünde bir CustomBinding > öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. CustomBinding > öğesinin içinde, `name` özniteliği olarak ayarlanmış`FederationDuplexTcpMessageSecurityBinding`bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. Bağlama > öğesinin içinde, `authenticationMode` özniteliği olarak ayarlanmış`SecureConversation`bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun. [ \<](../../../../docs/framework/misc/binding.md)

4. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` `IssuedTokenForCertificate` [ Güvenlik>öğesiiçinde,veyaolarakayarlananözniteliğiilebirsecurebir\<Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesioluşturun`IssuedTokenForSslNegotiated`.

5. Güvenlik > öğesini izleyerek boş [ \<bir TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için

1. Yapılandırma dosyasının [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlamalar > düğümünde bir CustomBinding > öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. CustomBinding > öğesinin içinde, `name` özniteliği olarak ayarlanmış`FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. Bağlama > öğesinin içinde, `authenticationMode` özniteliği olarak ayarlanmış`SecureConversation`bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun. [ \<](../../../../docs/framework/misc/binding.md)

4. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` `IssuedTokenForCertificate` [ Güvenlik>öğesiiçinde,veyaolarakayarlananözniteliğiilebirsecurebir\<Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesioluşturun`IssuedTokenForSslNegotiated`.

5. Güvenlik > öğesini izleyerek boş [ \<bir sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

6. SslStreamSecurity > öğesini izleyerek boş [ \<bir TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

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
