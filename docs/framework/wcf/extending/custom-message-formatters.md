---
title: Custom Message Formatters
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: e1633bdd3959ba812251ef1b78bcd0e83b2060c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612789"
---
# <a name="custom-message-formatters"></a>Custom Message Formatters
Bir ileti içeriği genellikle XML biçiminde, genellikle bir uygulama için uygun bir biçim değil. Uygulamaları başlama ve özelliklerini ayarlayarak nesneleri işleyin. Windows Communication Foundation (WCF) kullanan *veri anlaşması* dönüştürmek için bir <xref:System.ServiceModel.Channels.Message> nesnesine kolayca bir uygulama tarafından işlenen bir nesne. Bu işlemler, serileştirme ve seri durumundan çıkarma adı verilir. Bu aynı koşulları serileştirme açıklamak ve ilgisiz bir işlemdir ileti kablo biçimine veya biçiminden Aktarım katmanı tarafından yapılan seri durumdan çıkarma için kullanıldığını unutmayın.  
  
 İletileri ve bir veri sözleşmesi yoluyla yapamayacağınız nesneler arasında özel bir dönüştürme uygulamak gerekiyorsa, bir özel ileti biçimlendirici kullanabilirsiniz. Bunu değiştirerek veya bir istemci veya hizmet belirli sözleşme işlem yürütme davranışını genişletme yapın.  
  
## <a name="custom-message-formatters-on-the-client"></a>İstemci üzerinde özel ileti Biçimlendiriciler  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Arabirimi iletilere istemci uygulamaları için iletileri dönüştürme nesneleri ve nesnelerin denetlemek için kullanılan yöntemleri tanımlar.  
  
 Bu arabirim uygulamalıdır. İlk geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> yöntemi bir ileti seri durumdan çıkarılacak. Bu yöntem, bir gelen iletiyi aldıktan sonra ancak istemci işlemini dağıtılmasından önce çağrılır.  
  
 Ardından, geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> bir nesneyi serileştirmek için yöntemi. Bu yöntem, giden bir ileti göndermeden önce çağrılır.  
  
 Özel biçimlendirici hizmet uygulamasına eklemek için Ata <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> nesnesini <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> işlemi davranışını kullanarak özellik. Davranışlar hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Hizmeti üzerinde özel ileti Biçimlendiriciler  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimi tanımlar dönüştürme yöntemleri bir <xref:System.ServiceModel.Channels.Message> parametrelerinden ve bir işlem için parametre nesnesine bir <xref:System.ServiceModel.Channels.Message> hizmet uygulama nesnesi.  
  
 Bu arabirim uygulamalıdır. İlk geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> yöntemi bir ileti seri durumdan çıkarılacak. Bu yöntem, bir gelen iletiyi aldıktan sonra ancak istemci işlemini dağıtılmasından önce çağrılır.  
  
 Ardından, geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> bir nesneyi serileştirmek için yöntemi. Bu yöntem, giden bir ileti göndermeden önce çağrılır.  
  
 Özel biçimlendirici hizmet uygulamasına eklemek için Ata <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> nesnesini <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> işlemi davranışını kullanarak özellik. Davranışlar hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
