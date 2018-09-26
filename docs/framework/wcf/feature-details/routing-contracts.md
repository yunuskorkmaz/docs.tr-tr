---
title: Sözleşmeleri Yönlendirme
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 73d303c95a636f5e90f256272726c08c581d6fdf
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074972"
---
# <a name="routing-contracts"></a>Sözleşmeleri Yönlendirme
Yönlendirme sözleşmeleri yönlendirme hizmeti işleyebileceği ileti desenlerini tanımlayın.  Her sözleşme türsüz ve ileti Şeması veya eylem bilgisi olmadan bir ileti almak hizmet verir. Bu, genel temel alınan iletileri yönlendirilmek özellikleri için ek yapılandırma olmadan iletileri yönlendirmek yönlendirme hizmeti sağlar.  
  
## <a name="routing-contracts"></a>Sözleşmeleri Yönlendirme  
 Yönlendirme hizmeti, genel bir WCF ileti nesnesi kabul ettiğinden, sözleşme seçerken en önemli konu istemcileri ve Hizmetleri ile iletişim kurarken kullanılacak kanal şekildir. Yönlendirme hizmeti iletilerini işlerken simetrik ileti pompalara böylece genellikle gelen sözleşme şeklini giden sözleşme şeklini eşleşmelidir kullanır. Ancak, hizmet modelin dağıtıcı zaman dağıtıcı istek-yanıt kanala çift yönlü kanalı dönüştürür veya gibi gerekli değildir ve (yani kullanılmayan bir kanaldan oturum desteği kaldırır şekilleri, burada değiştirebilirsiniz durumlar vardır zaman **SessionMode.Allowed**, dönüştürme bir **IInputSessionChannel** içine bir **IInputChannel**).  
  
 Bu ileti pompalara desteklemek için sözleşmeleri yönlendirme hizmeti sağlayan <xref:System.ServiceModel.Routing> ad alanı yönlendirme hizmeti tarafından kullanılan hizmet uç noktaları tanımlarken kullanılmalıdır. Bu sözleşmeler türsüz, herhangi bir ileti türü veya eylem giriş sağlar ve belirli bir ileti şema bilgisi olmadan iletileri işlemek yönlendirme hizmeti sağlar. Yönlendirme hizmeti tarafından kullanılan sözleşmeleri hakkında daha fazla bilgi için bkz. [sözleşmeleri yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Yönlendirme hizmeti tarafından sağlanan sözleşmeleri bulunan <xref:System.ServiceModel.Routing> çalıştırdığınız ve ad alanı aşağıdaki tabloda açıklanan.  
  
|Daralma|Şekil|Kanal şekli|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode SessionMode.Allowed =<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel IOutputChannel ->|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|Sessionmode'u SessionMode.Required =<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel IOutputSessionChannel ->|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode SessionMode.Allowed =<br /><br /> AsyncPattern = true|IReplyChannel IRequestChannel ->|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|Da IDuplexSessionChannel öğelerini da IDuplexSessionChannel öğelerini ->|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Hizmeti](https://msdn.microsoft.com/library/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [Yönlendirme Tanıtımı](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
