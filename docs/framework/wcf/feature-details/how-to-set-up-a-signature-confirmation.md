---
title: 'Nasıl yapılır: Bir imza onayı ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 5163436f75e403ee7f682cdbe378922657116063
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513623"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Nasıl yapılır: Bir imza onayı ayarlama
*İmza onayı* alınan yanıtı gönderen kişinin orijinal iletiye yanıt olarak oluşturulan emin olmak bir ileti Başlatıcı bir mekanizmadır. İmza onayı WS-güvenlik 1.1 belirtiminde tanımlanır. Bir uç nokta WS-güvenlik 1.0 destekliyorsa, imza onayını kullanamazsınız.  
  
 Nasıl imza onayı kullanarak etkinleştirmek aşağıdaki yordamları belirtin bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Yordamın aynısını ile kullanabileceğiniz bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Bulunan temel adımları sırasında yordamı yapılar [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>İmza onayı kodda etkinleştirmek için  
  
1.  Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.  
  
2.  Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfı.  
  
3.  Ayarlama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> için `true`.  
  
4.  Güvenlik öğesinin bağlama koleksiyona ekleyin.  
  
5.  Belirtilen özel bir bağlama oluşturma [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>İmza onayı yapılandırması etkinleştirmek için  
  
1.  Ekleme bir `<customBinding>` öğesine `<bindings>` yapılandırma dosyasının.  
  
2.  Ekleme bir `<binding>` öğesi ve küme adı özniteliği için uygun bir değer.  
  
3.  Uygun bir kodlama öğesi ekleyin. Aşağıdaki örnek ekler bir `<TextMessageEncoding>` öğesi.  
  
4.  Ekleme bir `<security>` alt öğesi ve kümesi `requireSignatureConfirmation` özniteliğini `true`.  
  
5.  İsteğe bağlı. Önyükleme sırasında imza Onayı etkinleştirmek için eklemeniz bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğesi ve kümesi `equireSignatureConfirmation` özniteliğini `true`.  
  
6.  Uygun aktarma öğesini ekleyin. Aşağıdaki örnek ekler bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
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
 Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ayarlar <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> özelliğini `true`. Bu örnekte kullanmaz Not `<secureConversationBootstrap>` yukarıdaki örnekte gösterildiği gibi. Bu örnek, bir Windows (Kerberos protokolü) belirteci kullanıldığında imza onayı gösterir. Bu durumda, imza istemcinin hizmetinden alınan tüm yanıtları döndürülür ve istemci tarafından onaylanır.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
