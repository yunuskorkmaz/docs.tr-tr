---
title: Dijital İmzaların Şifrelenmesi
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: 41094b2eee50e97cf60887cfa29f8110f2895bfa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597403"
---
# <a name="encryption-of-digital-signatures"></a>Dijital İmzaların Şifrelenmesi
Varsayılan olarak, bir ileti imzalanır ve şifrelenir ve imza dijital olarak şifrelenir. Ya da bir örneği ile özel bir bağlama oluşturarak <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ardından `MessageProtectionOrder` her iki sınıfın özelliğini bir <xref:System.ServiceModel.Security.MessageProtectionOrder> sabit listesi değeri olarak ayarlayarak bunu kontrol edebilirsiniz. Varsayılan değer: <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu işlem, yalnızca imzalama ve şifreleme için 10 ila %40 sürer. Bununla birlikte imza şifrelemesini devre dışı bırakmak, bir saldırganın iletinin içeriğini tahmin etmesini sağlayabilir. Bu mümkündür çünkü imza öğesi iletideki her imzalı parçanın düz metnin karma kodunu içerir. Örneğin, ileti gövdesi varsayılan olarak şifrelense de şifrelenmemiş imza, ileti gövdesinin karma kodunu içerir. İleti küçükse, bir saldırgan içerikleri verebilir. İmzanın şifrelenmesi bu olasılığı azaltır veya ortadan kaldırır.  
  
 Bu nedenle, yalnızca içeriğin değeri düşük olduğunda imza şifrelemesini devre dışı bırakın ve örneğin güvenlik etkilerine sahip olmayan büyük ikili dosyalar gönderilirken performans kazancı önemli olur.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzalamayı devre dışı bırakmak için  
  
1. Oluşturun <xref:System.ServiceModel.Channels.CustomBinding> . Daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>Bağlama koleksiyonuna bir veya a ekleyin <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
3. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType>Özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> .  
  
 Özel Bağlamalar Oluşturma hakkında daha fazla bilgi için bkz. [Kullanıcı Tanımlı Bağlamalar Oluşturma](../extending/creating-user-defined-bindings.md). Belirli bir kimlik doğrulama modu için özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: belirtilen bir kimlik doğrulama modu Için SecurityBindingElement oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Kullanıcı Tanımlı Bağlamalar Oluşturma](../extending/creating-user-defined-bindings.md)
- [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
