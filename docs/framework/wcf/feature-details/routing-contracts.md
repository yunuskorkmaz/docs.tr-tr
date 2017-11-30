---
title: "Sözleşmeleri Yönlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: daebd84c9cef5e64ea7ed55c27b671ba01d14df0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="routing-contracts"></a>Sözleşmeleri Yönlendirme
Yönlendirme sözleşmeleri yönlendirme hizmeti işleyebilir ileti desenleri tanımlayın.  Her sözleşme yazısız ve ileti Şeması veya eylem bilgisine olmadan bir ileti almak hizmet sağlar. Bu genel yönlendirilen temel alınan iletilerin özellikleri için ek yapılandırma olmadan iletileri yönlendirmek yönlendirme hizmeti sağlar.  
  
## <a name="routing-contracts"></a>Sözleşmeleri Yönlendirme  
 Yönlendirme hizmeti genel bir WCF ileti nesneyi kabul ettiğinden, bir sözleşme seçerken en önemli istemcileri ve Hizmetleri ile iletişim kurarken kullanılacak kanalı şeklini konudur. İletilerini işlerken yönlendirme hizmeti simetrik ileti Pompalar, bu nedenle genellikle gelen sözleşme şeklini giden sözleşme şeklini eşleşmelidir kullanır. Ancak, hizmet modelinin dağıtıcısı zaman dağıtıcı çift yönlü bir kanal bir istek-yanıt kanal dönüştürür veya gibi gerekli değildir ve (yani kullanılmayan bir kanaldan oturum desteğini kaldırır şekiller, burada değiştirebilirsiniz durumlar vardır zaman **SessionMode.Allowed**, dönüştürme bir **IInputSessionChannel** içine bir **IInputChannel**).  
  
 Bu ileti Pompalar desteklemek için yönlendirme hizmeti sözleşmelerinde sağlar <xref:System.ServiceModel.Routing> ad alanı yönlendirme hizmeti tarafından kullanılan hizmet uç noktalarına tanımlarken kullanılmalıdır. Bu sözleşmeler yazısız,, herhangi bir ileti türü veya eylemi alınmasını sağlar ve belirli bir ileti şema bilgisi olmadan iletileri işlemek yönlendirme hizmeti sağlar. Yönlendirme hizmeti tarafından kullanılan sözleşmeleri hakkında daha fazla bilgi için bkz: [sözleşmeleri yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Yönlendirme hizmeti tarafından sağlanan sözleşmeleri bulunan <xref:System.ServiceModel.Routing> ad alanı ve bu aşağıdaki tabloda açıklanan.  
  
|Daralma|Şekil|Kanal şekli|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode SessionMode.Allowed =<br /><br /> Başlatıcıda = true<br /><br /> IsOneWay = true|IInputChannel IOutputChannel ->|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode SessionMode.Required =<br /><br /> Başlatıcıda = true<br /><br /> IsOneWay = true|IInputSessionChannel IOutputSessionChannel ->|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode SessionMode.Allowed =<br /><br /> Başlatıcıda = true|IReplyChannel IRequestChannel ->|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> Başlatıcıda = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|Da IDuplexSessionChannel öğelerini da IDuplexSessionChannel öğelerini ->|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme hizmeti](http://msdn.microsoft.com/en-us/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [Yönlendirme Tanıtımı](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
