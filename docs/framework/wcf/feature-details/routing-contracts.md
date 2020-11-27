---
title: Sözleşmeleri Yönlendirme
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 4c75034a8fdbf02bf568bc5392361113a37427be
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295502"
---
# <a name="routing-contracts"></a>Sözleşmeleri Yönlendirme

Yönlendirme sözleşmeleri, yönlendirme hizmetinin işleyebildiğiniz ileti düzenlerini tanımlar.  Her sözleşme türsüz olur ve hizmetin ileti Şeması veya eylem bilgisine sahip olmayan bir ileti almasına izin verir. Bu, yönlendirme hizmetinin yönlendirmekte olan temeldeki iletilerin özellikleri için ek yapılandırma gerektirmeden iletileri genel olarak yol açmasına olanak sağlar.  
  
## <a name="routing-contracts"></a>Sözleşmeleri Yönlendirme  

 Yönlendirme hizmeti genel bir WCF Ileti nesnesini kabul ettiğinden, bir sözleşmeyi seçerken en önemli nokta, istemciler ve hizmetlerle iletişim kurarken kullanılacak kanalın şekilidir. İletileri işlerken, yönlendirme hizmeti simetrik ileti pumps kullanır, bu nedenle genellikle gelen sözleşmenin şeklinin giden sözleşmenin şekliyle eşleşmesi gerekir. Ancak, hizmet modeli dağıtıcısında, dağıtıcı bir çift yönlü kanalı bir istek-yanıt kanalına dönüştürdüğünde veya **gerekmediği zaman bir** kanaldan oturum desteğini kaldıran (yani, bir **IInputSessionChannel** bir **IInputChannel**'a dönüştürülürken), bu şekilde şekilleri değiştirebilecekleri durumlar vardır.  
  
 Bu ileti pumps 'leri desteklemek için, yönlendirme hizmeti, <xref:System.ServiceModel.Routing> yönlendirme hizmeti tarafından kullanılan hizmet uç noktaları tanımlanırken kullanılması gereken ad alanı içinde sözleşmeler sağlar. Bu sözleşmeler, herhangi bir ileti türü veya eyleminin alınabileceği ve yönlendirme hizmetinin belirli ileti şeması hakkında bilgi sahibi olmayan iletileri işlemesine izin veren türsüz bir işlemdir. Yönlendirme hizmeti tarafından kullanılan sözleşmeler hakkında daha fazla bilgi için bkz. [yönlendirme sözleşmeleri](routing-contracts.md).  
  
 Yönlendirme hizmeti tarafından sunulan sözleşmeler <xref:System.ServiceModel.Routing> ad alanında bulunur ve aşağıdaki tabloda açıklanmıştır.  
  
|Anlaşma|Şekil|Kanal şekli|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode. Allowed<br /><br /> Asyncmodel = true<br /><br /> IsOneWay = true|IInputChannel-> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> Asyncmodel = true<br /><br /> IsOneWay = true|IInputSessionChannel-> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode. Allowed<br /><br /> Asyncmodel = true|IReplyChannel destekleyen desteklenecektir-> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> CallbackContract = typeof (ısımplexsession)<br /><br /> Asyncmodel = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow (TransactionFlowOption. Allowed)|IDuplexSessionChannel-> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Hizmeti](routing-service.md)
- [Yönlendirme Tanıtımı](routing-introduction.md)
