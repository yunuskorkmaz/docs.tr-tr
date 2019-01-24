---
title: Dijital İmzaların Şifrelenmesi
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: c3d780ce823c42874f001b0adcfc36b018e32a2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529796"
---
# <a name="encryption-of-digital-signatures"></a>Dijital İmzaların Şifrelenmesi
Varsayılan olarak, bir ileti imzalanacak ve şifrelenecek ve imza dijital olarak şifrelenir. Bu örneği ile özel bir bağlama oluşturarak denetim <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ardından ayarlar `MessageProtectionOrder` özelliği için ya da sınıfın bir <xref:System.ServiceModel.Security.MessageProtectionOrder> numaralandırma değeri. Varsayılan, <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> değeridir. Bu işlem, yüzde 10 40'ı için basitçe imzalama ve şifreleme daha uzun sürer. Şifreleme imzası devre dışı bırakıldığında, ancak iletinin içeriğini tahmin etmek bir saldırgan sağlayabilir. İmza öğesi düz metin iletisi imzalı her bölümü karma kodunu içerdiğinden, bu mümkündür. Örneğin, ileti gövdesi, varsayılan olarak şifrelenmiş olsa da, şifrelenmemiş imza karma kodunu ileti gövdesi içeriyor. İleti küçükse, bir saldırganın içeriği türetme mümkün olabilir. Şifreleme imzası küçültür veya bu olanağına ortadan kaldırır.  
  
 Bu nedenle, şifreleme imzası yalnızca içeriğin değerinin düşük olduğu ve performans gibi hiçbir güvenlikle ilgili etkileri olan büyük ikili dosyaları gönderirken önemli olacaktır devre dışı bırakın.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzasını devre dışı bırakmak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Channels.CustomBinding>. Daha fazla bilgi için [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Ekleyin ya da bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bağlama koleksiyonuna.  
  
3.  Ayarlama <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 Özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Özel kimlik doğrulama modu için özel bir bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
