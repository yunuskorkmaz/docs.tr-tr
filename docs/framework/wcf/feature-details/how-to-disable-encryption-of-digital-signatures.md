---
title: 'Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 074a32f6a69f8353568e76c99f4b65aece813f55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491666"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma
Varsayılan olarak, bir ileti imzalanır ve imza dijital olarak şifrelenir. Bu örneği ile özel bağlama oluşturarak denetlenir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ayarı `MessageProtectionOrder` özelliği için her iki sınıfın bir <xref:System.ServiceModel.Security.MessageProtectionOrder> numaralandırma değeri. Varsayılan, <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> değeridir. Bu işlem yalnızca imzalama değerinden daha uzun yüzde 30 tüketir ve şifreleme Genel ileti (daha küçük ileti, daha büyük performans etkisi) boyutuna göre. İmza şifrelemeyi devre dışı bırakmak ancak, bir saldırganın iletinin içeriğini tahmin sağlayabilir. Düz metin iletisi imzalı her bölümünün karma kodunu imza öğesi içerdiği için bu mümkün olur. Örneğin, varsayılan ileti gövdesi şifrelenmesine rağmen şifrelenmemiş imza ileti gövdesi şifreleme önce karma kodunu içerir. İmzalanmış ve şifrelenmiş bölümü için olası değerler kümesi küçükse, bir saldırganın karma değer bakarak içeriği türetme olabilir. İmza şifreleme bu saldırı vektörü azaltır.  
  
 Bu nedenle, şifreleme imza yalnızca içeriğin düşük değeri veya olası içerik değerleri büyük ve belirleyici kümesidir ve performans kazancı yukarıda açıklanan saldırı Azaltıcı daha fazla önemlidir devre dışı bırakın.  
  
> [!NOTE]
>  Varsa hiçbir şey şifrelenir iletide, imza öğesi şifrelenmez, bile <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu davranış, hatta sistem tarafından sağlanan bağlamalar ile oluşur; tüm sistem tarafından sağlanan bağlamaları kümesine ileti koruma sırasını sahip `SignBeforeEncryptAndEncryptSignature`. Ancak, Web Hizmetleri Açıklama Dili (WSDL) WCF oluşturur içermeye devam `<sp:EncryptSignature>` onaylama.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzasını devre dışı bırakmak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Channels.CustomBinding>. Daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Ekleyip ya da bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bağlama koleksiyonuna.  
  
3.  Ayarlama <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
