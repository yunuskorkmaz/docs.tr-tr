---
title: Custom Message Formatters
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: 9f66071d3c400ca2adc615afc7f93b2483fe2136
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795804"
---
# <a name="custom-message-formatters"></a>Custom Message Formatters
Bir iletideki içerik genellikle, genellikle bir uygulama için kolay bir biçim olmayan XML biçiminde olur. Uygulamalar nesneleri işleyebilir, özelliklerini alıyor ve ayarlar. Windows Communication Foundation (WCF), bir <xref:System.ServiceModel.Channels.Message> nesneyi bir uygulama tarafından kolayca işlenen nesneye dönüştürmek için *veri sözleşmesini* kullanır. Bu işlemlere serileştirme ve seri durumundan çıkarma denir. Bu koşulların, ilişkili olmayan bir işlem olan ileti tel biçiminden ve Aktarım katmanı tarafından gerçekleştirilen serileştirme ve seri durumdan çıkarma işlemini açıklayan şekilde kullanıldığını unutmayın.  
  
 Bir veri sözleşmesi aracılığıyla gerçekleştiremeyeceğiniz iletiler ve nesneler arasında özelleştirilmiş bir dönüştürme uygulamanız gerekiyorsa özel bir ileti biçimlendirici kullanabilirsiniz. Bu işlemi, bir istemci veya hizmette belirli bir sözleşme işleminin yürütme davranışını değiştirerek veya genişleterek yapın.  
  
## <a name="custom-message-formatters-on-the-client"></a>Istemcideki özel Ileti formatları  
 Arabirim <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> , istemci uygulamalarına yönelik iletilere iletileri nesnelere ve nesnelere dönüştürmeyi denetlemek için kullanılan yöntemleri tanımlar.  
  
 Bu arabirimi uygulamanız gerekir. İlk olarak, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> bir iletinin serisini kaldırmak için yöntemi geçersiz kılın. Bu yöntem, gelen bir ileti alındıktan sonra, istemci işlemine dağıtılmadan önce çağrılır.  
  
 Sonra, bir nesneyi <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> seri hale getirmek için yöntemini geçersiz kılın. Bu yöntem, giden bir ileti gönderilmeden önce çağrılır.  
  
 Özel biçimlendirici hizmetini hizmet uygulamasına eklemek için, bir işlem davranışı kullanarak <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> nesnesini <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> özelliğine atayın. Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Hizmette özel Ileti formatları  
 Arabirim <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> , bir <xref:System.ServiceModel.Channels.Message> nesneyi bir işlem için parametrelere ve parametrelerden bir hizmet uygulamasındaki bir <xref:System.ServiceModel.Channels.Message> nesneye dönüştüren yöntemleri tanımlar.  
  
 Bu arabirimi uygulamanız gerekir. İlk olarak, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> bir iletinin serisini kaldırmak için yöntemi geçersiz kılın. Bu yöntem, gelen bir ileti alındıktan sonra, istemci işlemine dağıtılmadan önce çağrılır.  
  
 Sonra, bir nesneyi <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> seri hale getirmek için yöntemini geçersiz kılın. Bu yöntem, giden bir ileti gönderilmeden önce çağrılır.  
  
 Özel biçimlendirici hizmetini hizmet uygulamasına eklemek için, bir işlem davranışı kullanarak <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> nesnesini <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> özelliğine atayın. Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](configuring-and-extending-the-runtime-with-behaviors.md)
