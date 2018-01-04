---
title: Custom Message Formatters
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea32656db90907ae523502fc1796466442ef4a4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-formatters"></a>Custom Message Formatters
Bir ileti içeriği XML biçiminde, genellikle bir uygulama için uygun bir biçim değil görülür. Uygulamaları alma ve bunların özelliklerini ayarlama nesnelerini yönetme. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]kullanan *veri sözleşmesi* dönüştürmek için bir <xref:System.ServiceModel.Channels.Message> nesnesine kolayca bir uygulama tarafından işlenen bir nesne. Bu işlemler, seri hale getirme ve seri durumdan çıkarma denir. Bu aynı koşulları serileştirme tanımlamak ve Aktarım katmanı ilişkisiz bir işlemdir ileti gönderme biçimini gelen ve giden yapılır seri durumundan çıkarma için kullanıldığını unutmayın.  
  
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
