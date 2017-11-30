---
title: "Nasıl yapılır: İmza Onayı Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1cf2048a630b3556291577565bed47c40665b156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Nasıl yapılır: İmza Onayı Ayarlama
*İmza onayı* alınan yanıt gönderenin özgün iletisine yanıt olarak oluşturulan emin olmak bir ileti başlatıcı için bir mekanizmadır. İmza onayı WS güvenliği 1.1 belirtimini tanımlanır. Bir uç nokta WS güvenliği 1.0 destekliyorsa, imza onayı kullanamazsınız.  
  
 Aşağıdaki yordamlar imza onayı kullanarak etkinleştirmek nasıl belirtin bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Yordamın aynısını ile kullanabileceğiniz bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Bulunan temel adımlar üzerine yordamı derlemeler [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>İmza onayı kodda etkinleştirmek için  
  
1.  Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.  
  
2.  Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfı.  
  
3.  Ayarlama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> için `true`.  
  
4.  Güvenlik öğesinin bağlama koleksiyona ekleyin.  
  
5.  Belirtildiği gibi özel bağlama oluşturma [nasıl yapılır: SecurityBindingElement kullanarak özel bir bağlama oluşturun](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>İmza onayı yapılandırmasında etkinleştirmek için  
  
1.  Ekleme bir `<customBinding>` öğesine `<bindings>` yapılandırma dosyasının.  
  
2.  Ekleme bir `<binding>` öğesi ve kümesi adı özniteliği için uygun bir değer.  
  
3.  Uygun kodlama öğe ekleyin. Aşağıdaki örnek, bir `<TextMessageEncoding>` öğesi.  
  
4.  Ekleme bir `<security>` alt öğesi ve kümesi `requireSignatureConfirmation` özniteliğini `true`.  
  
5.  İsteğe bağlı. İmza onayı önyükleme sırasında etkinleştirmek için add bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğesi ve kümesi `equireSignatureConfirmation` özniteliğini `true`.  
  
6.  Uygun bir taşıma öğe ekleyin. Aşağıdaki örnek, bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
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
 Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ayarlar <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> özelliğine `true`. Bu örnek kullanmayan Not `<secureConversationBootstrap>` önceki örnekte gösterilen öğesi. Bu örnek, bir Windows (Kerberos protokolü) belirteci kullanırken imza onayı gösterir. Bu durumda, istemcinin imza hizmetinden tüm yanıtları döndürülür ve istemci tarafından doğrulanır.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
