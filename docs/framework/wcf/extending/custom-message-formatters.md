---
title: Custom Message Formatters
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: 301c508a0c639985e226dc55f62431ad8bb9c12b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-message-formatters"></a>Custom Message Formatters
Bir ileti içeriği XML biçiminde, genellikle bir uygulama için uygun bir biçim değil görülür. Uygulamaları alma ve bunların özelliklerini ayarlama nesnelerini yönetme. Windows Communication Foundation (WCF) kullanan *veri sözleşmesi* dönüştürmek için bir <xref:System.ServiceModel.Channels.Message> nesnesine kolayca bir uygulama tarafından işlenen bir nesne. Bu işlemler, seri hale getirme ve seri durumdan çıkarma denir. Bu aynı koşulları serileştirme tanımlamak ve Aktarım katmanı ilişkisiz bir işlemdir ileti gönderme biçimini gelen ve giden yapılır seri durumundan çıkarma için kullanıldığını unutmayın.  
  
 İletileri ve bir veri sözleşmesi yoluyla yapamayacağınız nesneler arasında özel bir dönüştürme uygulamanız gerekiyorsa, özel ileti biçimlendirici kullanabilirsiniz. Bunu, değiştirerek veya bir istemci veya hizmet belirli sözleşme işlemi yürütme davranışını genişletme yapabilirsiniz.  
  
## <a name="custom-message-formatters-on-the-client"></a>Özel ileti Biçimlendiricileri istemcide  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Arabirimi iletilerine istemci uygulamaları için ve nesneleri iletileri dönüştürmek denetlemek için kullanılan yöntemleri tanımlar.  
  
 Bu arabirimi uygulamalıdır. İlk geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> bir ileti seri durumdan çıkarılacak yöntemi. Bu yöntem, bir gelen iletiyi aldıktan sonra ancak istemci işlemini dağıtılmasından önce çağrılır.  
  
 Ardından, geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> bir nesneyi serileştirme yöntemi. Bu yöntem, giden bir iletiyi göndermeden önce çağrılır.  
  
 Özel biçimlendirici hizmet uygulamasına eklemek için Ata <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> nesnesine <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> işlemi davranışı kullanarak özelliği. Davranışları hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Özel ileti Biçimlendiricileri hizmeti hakkında  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimi tanımlar dönüştürme yöntemleri bir <xref:System.ServiceModel.Channels.Message> bir işlem için ve parametrelerinden parametreleri nesnesine bir <xref:System.ServiceModel.Channels.Message> bir hizmet uygulaması nesnesinde.  
  
 Bu arabirimi uygulamalıdır. İlk geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> bir ileti seri durumdan çıkarılacak yöntemi. Bu yöntem, bir gelen iletiyi aldıktan sonra ancak istemci işlemini dağıtılmasından önce çağrılır.  
  
 Ardından, geçersiz kılma <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> bir nesneyi serileştirme yöntemi. Bu yöntem, giden bir iletiyi göndermeden önce çağrılır.  
  
 Özel biçimlendirici hizmet uygulamasına eklemek için Ata <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> nesnesine <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> işlemi davranışı kullanarak özelliği. Davranışları hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
