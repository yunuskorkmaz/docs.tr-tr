---
title: 'Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: e2fd2a058e636ebf398f9d0c71a93788ccd7dfa0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325273"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma
Varsayılan olarak, bir iletinin imzalanmış ve imza dijital olarak şifrelenir. Bu örneği ile özel bir bağlama oluşturarak denetlenir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ayarı `MessageProtectionOrder` özelliği için ya da sınıfın bir <xref:System.ServiceModel.Security.MessageProtectionOrder> numaralandırma değeri. Varsayılan, <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> değeridir. Bu işlem yalnızca imzalama değerinden daha fazla zaman yüzde 30 kullanır ve genel iletinin (ileti daha küçük, büyük performans etkisi) boyutuna göre şifreleme. Şifreleme imzası devre dışı bırakıldığında, ancak iletisinin içeriği tahmin etmek bir saldırgan sağlayabilir. İmza öğesi düz metin iletisi imzalı her bölümü karma kodunu içerdiğinden, bu mümkündür. Örneğin, ileti gövdesi, varsayılan olarak şifrelenmiş olsa da, şifrelenmemiş imza karma kodunu şifreleme önce ileti gövdesi içeriyor. İmzalanmış ve şifrelenmiş bölümü için olası değerler kümesini küçük olursa, bir saldırganın karma değer bakarak, içeriği türetme mümkün olabilir. Şifreleme imzası bu saldırı vektörü azaltır.  
  
 Bu nedenle, şifreleme imzası yalnızca içeriğin değerinin düşük olduğu veya büyük ve belirleyici olmayan içerik olası değerler kümesidir ve performans kazancı daha yukarıda açıklanan saldırı azaltma daha önemli devre dışı bırakın.  
  
> [!NOTE]
>  İmza öğesi yoksa hiçbir şey şifrelenir iletide, şifreli değil, bile <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu davranış, sistem tarafından sağlanan bağlamaları ile bile oluşur; tüm sistem tarafından sağlanan bağlamalar kümesine iletisi koruma olması `SignBeforeEncryptAndEncryptSignature`. Ancak, Web Hizmetleri Açıklama Dili (WSDL) WCF oluşturur içermeye devam `<sp:EncryptSignature>` onaylama.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzasını devre dışı bırakmak için  
  
1. Oluşturma bir <xref:System.ServiceModel.Channels.CustomBinding>. Daha fazla bilgi için [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Ekleyin ya da bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bağlama koleksiyonuna.  
  
3. Ayarlama <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
