---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Imza onayı ayarlama'
title: 'Nasıl yapılır: İmza Onayı Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 158ec2a5f74038f5c1ca1af847f57457a8881974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643195"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Nasıl yapılır: İmza Onayı Ayarlama

*İmza onaylama* bir ileti başlatıcısının, gönderenin özgün iletisine yanıt olarak alınan bir yanıtın oluşturulduğundan emin olmak için bir mekanizmadır. İmza onayı WS-Security 1,1 belirtiminde tanımlanmıştır. Bir uç nokta WS-Security 1,0 destekliyorsa, imza onayını kullanamazsınız.

Aşağıdaki yordamlar, kullanarak imza onayını etkinleştirmeyi belirtir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . İle aynı yordamı kullanabilirsiniz <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Yordamı, [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)bölümünde bulunan temel adımların üzerine oluşturulur.

### <a name="to-enable-signature-confirmation-in-code"></a>Kodda imza onayını etkinleştirmek için

1. Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.

2. Sınıfının bir örneğini oluşturun  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .

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
