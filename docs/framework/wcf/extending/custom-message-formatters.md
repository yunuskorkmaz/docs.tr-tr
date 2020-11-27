---
title: Custom Message Formatters
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: e238eb134772c0a95934a460edda62ca9dba2518
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254771"
---
# <a name="custom-message-formatters"></a>Custom Message Formatters

Bir iletideki içerik genellikle, genellikle bir uygulama için kolay bir biçim olmayan XML biçiminde olur. Uygulamalar nesneleri işleyebilir, özelliklerini alıyor ve ayarlar. Windows Communication Foundation (WCF), bir nesneyi bir uygulama tarafından kolayca işlenen nesneye dönüştürmek için *veri sözleşmesini* kullanır <xref:System.ServiceModel.Channels.Message> . Bu işlemlere serileştirme ve seri durumundan çıkarma denir. Bu koşulların, ilişkili olmayan bir işlem olan ileti tel biçiminden ve Aktarım katmanı tarafından gerçekleştirilen serileştirme ve seri durumdan çıkarma işlemini açıklayan şekilde kullanıldığını unutmayın.  
  
 Bir veri sözleşmesi aracılığıyla gerçekleştiremeyeceğiniz iletiler ve nesneler arasında özelleştirilmiş bir dönüştürme uygulamanız gerekiyorsa özel bir ileti biçimlendirici kullanabilirsiniz. Bu işlemi, bir istemci veya hizmette belirli bir sözleşme işleminin yürütme davranışını değiştirerek veya genişleterek yapın.  
  
## <a name="custom-message-formatters-on-the-client"></a>Istemcideki özel Ileti formatları  

 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>Arabirim, istemci uygulamalarına yönelik iletilere iletileri nesnelere ve nesnelere dönüştürmeyi denetlemek için kullanılan yöntemleri tanımlar.  
  
 Bu arabirimi uygulamanız gerekir. İlk olarak, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> bir iletinin serisini kaldırmak için yöntemi geçersiz kılın. Bu yöntem, gelen bir ileti alındıktan sonra, istemci işlemine dağıtılmadan önce çağrılır.  
  
 Sonra, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> bir nesneyi seri hale getirmek için yöntemini geçersiz kılın. Bu yöntem, giden bir ileti gönderilmeden önce çağrılır.  
  
 Özel biçimlendirici hizmetini hizmet uygulamasına eklemek için, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> bir işlem davranışı kullanarak nesnesini özelliğine atayın. Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Hizmette özel Ileti formatları  

 Arabirim, bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> <xref:System.ServiceModel.Channels.Message> nesneyi bir işlem için parametrelere ve parametrelerden bir hizmet uygulamasındaki bir nesneye dönüştüren yöntemleri tanımlar <xref:System.ServiceModel.Channels.Message> .  
  
 Bu arabirimi uygulamanız gerekir. İlk olarak, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> bir iletinin serisini kaldırmak için yöntemi geçersiz kılın. Bu yöntem, gelen bir ileti alındıktan sonra, istemci işlemine dağıtılmadan önce çağrılır.  
  
 Sonra, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> bir nesneyi seri hale getirmek için yöntemini geçersiz kılın. Bu yöntem, giden bir ileti gönderilmeden önce çağrılır.  
  
 Özel biçimlendirici hizmetini hizmet uygulamasına eklemek için, <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> bir işlem davranışı kullanarak nesnesini özelliğine atayın. Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](configuring-and-extending-the-runtime-with-behaviors.md)
