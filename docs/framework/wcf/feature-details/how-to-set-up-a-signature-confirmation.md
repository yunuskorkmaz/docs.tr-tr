---
title: 'Nasıl yapılır: İmza Onayı Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586929"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Nasıl yapılır: İmza Onayı Ayarlama

*İmza onaylama* bir ileti başlatıcısının, gönderenin özgün iletisine yanıt olarak alınan bir yanıtın oluşturulduğundan emin olmak için bir mekanizmadır. İmza onayı WS-Security 1,1 belirtiminde tanımlanmıştır. Bir uç nokta WS-Security 1,0 ' i destekliyorsa, imza onayını kullanamazsınız.

Aşağıdaki yordamlar, kullanarak imza onayını etkinleştirmeyi belirtir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . İle aynı yordamı kullanabilirsiniz <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Yordamı, [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)bölümünde bulunan temel adımların üzerine oluşturulur.

### <a name="to-enable-signature-confirmation-in-code"></a>Kodda imza onayını etkinleştirmek için

1. Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.

2. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .

3. Öğesini <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> olarak ayarlayın `true` .

4. Bağlama koleksiyonuna güvenlik öğesi ekleyin.

5. [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)bölümünde belirtildiği gibi özel bir bağlama oluşturun.

### <a name="to-enable-signature-confirmation-in-configuration"></a>Yapılandırmada imza onayını etkinleştirmek için

1. `<customBinding>` `<bindings>` Yapılandırma dosyasının bölümüne bir öğesi ekleyin.

2. Bir `<binding>` öğesi ekleyin ve Name özniteliğini uygun bir değere ayarlayın.

3. Uygun bir kodlama öğesi ekleyin. Aşağıdaki örnek bir öğesi ekler `<TextMessageEncoding>` .

4. Bir `<security>` alt öğesi ekleyin ve `requireSignatureConfirmation` özniteliğini olarak ayarlayın `true` .

5. İsteğe bağlı. Önyükleme sırasında imza onayını etkinleştirmek için bir [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğe ekleyin ve `requireSignatureConfirmation` özniteliğini olarak ayarlayın `true` .

6. Uygun bir taşıma öğesi ekleyin. Aşağıdaki örnek şunu ekler [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :

    ```xml
    <bindings>
      <customBinding>
        <binding name="SignatureConfirmationBinding">
          <security requireSignatureConfirmation="true">
            <secureConversationBootstrap requireSignatureConfirmation="true" />
              </security>
           <textMessageEncoding />
             <httpTransport />
        </binding>
      </customBinding>
    </bindings>
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> özelliğini olarak ayarlar `true` . Bu örneğin, `<secureConversationBootstrap>` Önceki örnekte gösterilen öğesini kullanmadığını unutmayın. Bu örnekte, bir Windows (Kerberos protokolü) belirteci kullanılırken imza onayı gösterilmektedir. Bu durumda, istemcinin imzası hizmetten gelen tüm yanıtlardan döndürülür ve istemci tarafından onaylanır.

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
