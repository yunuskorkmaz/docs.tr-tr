---
title: 'Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 461c5af2c7fbb98486a8decbe4aa998d8d21070d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911173"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma
Varsayılan olarak, bir ileti imzalanır ve imza dijital olarak şifrelenir. Bu, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> `MessageProtectionOrder` veya öğesinin bir örneği ile özel bir bağlama oluşturularak <xref:System.ServiceModel.Security.MessageProtectionOrder> veherikisınıfınözelliğinibirnumaralandırmadeğerineayarlayarakdenetlenir.<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> Varsayılan, <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> değeridir. Bu işlem, genel ileti boyutuna bağlı olarak yalnızca% 30 ' a kadar daha fazla zaman harcar (ileti daha küçük, performans etkisi artar). Bununla birlikte imza şifrelemesini devre dışı bırakmak, bir saldırganın iletinin içeriğini tahmin edemesine izin verebilir. Bu mümkündür çünkü imza öğesi iletideki her imzalı parçanın düz metnin karma kodunu içerir. Örneğin, ileti gövdesi varsayılan olarak şifrelense de şifrelenmemiş imza, şifrelemeden önceki ileti gövdesinin karma kodunu içerir. İmzalı ve şifreli bölüm için olası değerler kümesi küçükse, bir saldırgan karma değere bakarak içeriği verebilir. İmzayı şifrelemek, bu saldırı vektörünü azaltır.  
  
 Bu nedenle, imza şifrelemesini yalnızca içeriğin değeri düşük olduğunda veya olası içerik değerlerinin kümesi büyük ve belirleyici olmayan bir şekilde devre dışı bırakır ve performans kazancı yukarıda açıklanan saldırıları azaltmaya kıyasla daha önemlidir.  
  
> [!NOTE]
> Şifrelenmiş iletide hiçbir şey yoksa, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliği olarak <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>ayarlanmış olsa bile imza öğesi şifrelenmez. Bu davranış, sistem tarafından sağlanmış bağlamalarla da oluşur; sistem tarafından sağlanmış tüm bağlamalarda ileti koruma sırası olarak `SignBeforeEncryptAndEncryptSignature`ayarlanır. Ancak, Web Hizmetleri Açıklama Dili (wsdl) WCF oluşturur, hala `<sp:EncryptSignature>` onaylama işlemi içerir.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzalamayı devre dışı bırakmak için  
  
1. Oluşturma bir <xref:System.ServiceModel.Channels.CustomBinding>. Daha fazla bilgi için [nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)kullanarak özel bir bağlama oluşturun.  
  
2. Bağlama koleksiyonuna bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ekleyin.  
  
3. Özelliğini olarak <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>ayarlayın veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğini olarak<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>ayarlayın. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
