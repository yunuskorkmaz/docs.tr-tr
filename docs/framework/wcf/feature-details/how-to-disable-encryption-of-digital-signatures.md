---
title: 'Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 7ef305fdfd9a4ee61dfd89fdd46f2dc03a350977
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595407"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma
Varsayılan olarak, bir ileti imzalanır ve imza dijital olarak şifrelenir. Bu, veya öğesinin bir örneği ile özel bir bağlama oluşturularak <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve `MessageProtectionOrder` her iki sınıfın özelliğini bir <xref:System.ServiceModel.Security.MessageProtectionOrder> numaralandırma değerine ayarlayarak denetlenir. Varsayılan değer: <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu işlem, genel ileti boyutuna bağlı olarak yalnızca %30 ' a kadar daha fazla zaman harcar (ileti daha küçük, performans etkisi artar). Bununla birlikte imza şifrelemesini devre dışı bırakmak, bir saldırganın iletinin içeriğini tahmin edemesine izin verebilir. Bu mümkündür çünkü imza öğesi iletideki her imzalı parçanın düz metnin karma kodunu içerir. Örneğin, ileti gövdesi varsayılan olarak şifrelense de şifrelenmemiş imza, şifrelemeden önceki ileti gövdesinin karma kodunu içerir. İmzalı ve şifreli bölüm için olası değerler kümesi küçükse, bir saldırgan karma değere bakarak içeriği verebilir. İmzayı şifrelemek, bu saldırı vektörünü azaltır.  
  
 Bu nedenle, imza şifrelemesini yalnızca içeriğin değeri düşük olduğunda veya olası içerik değerlerinin kümesi büyük ve belirleyici olmayan bir şekilde devre dışı bırakır ve performans kazancı yukarıda açıklanan saldırıları azaltmaya kıyasla daha önemlidir.  
  
> [!NOTE]
> Şifrelenmiş iletide hiçbir şey yoksa, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliği olarak ayarlanmış olsa bile imza öğesi şifrelenmez <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> . Bu davranış, sistem tarafından sağlanmış bağlamalarla da oluşur; sistem tarafından sağlanmış tüm bağlamalarda ileti koruma sırası olarak ayarlanır `SignBeforeEncryptAndEncryptSignature` . Ancak, Web Hizmetleri Açıklama Dili (WSDL) WCF oluşturur, hala `<sp:EncryptSignature>` onaylama işlemi içerir.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzalamayı devre dışı bırakmak için  
  
1. Oluşturun <xref:System.ServiceModel.Channels.CustomBinding> . Daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>Bağlama koleksiyonuna bir veya a ekleyin <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
3. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType>Özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağlamalarla Güvenlik Özellikleri](security-capabilities-with-custom-bindings.md)
