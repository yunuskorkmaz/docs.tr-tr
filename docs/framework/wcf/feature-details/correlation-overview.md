---
title: "Bağıntı Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56b6252188854374b9e0eddd7aca53daba6f6086
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="correlation-overview"></a>Bağıntı Genel Bakış
Bağıntı bir sipariş işleme iş akışı kalıcı durum için iş akışı hizmeti iletileri birbirleriyle veya uygulama örneği durumu ilk isteğine yanıt ya da bir sıra kimliği gibi ilgili mekanizmadır. Bu konu bağıntı genel bir bakış sağlar. Bu bölümdeki diğer konulara bağıntı her tür için ek bilgileri sağlayın.  
  
## <a name="types-of-correlation"></a>Bağıntı türleri  
 Bağıntı protokol tabanlı veya içerik tabanlı olabilir. Protokol tabanlı bağıntıları ileti teslim altyapısı tarafından sağlanan veri iletileri arasında eşleme sağlamak için kullanın. Protokol tabanlı bağıntı kullanılarak bağıntılı iletileri ilgili birbirlerine nesneyi bellekte gibi kullanarak bir <xref:System.ServiceModel.Channels.RequestContext>, veya aktarım iletişim kuralı tarafından sağlanan bir belirteç. İçerik tabanlı bağıntıları birbirlerine ileti uygulama belirtilen verileri kullanarak ilgilidir. İçerik tabanlı bağıntı kullanılarak bağıntılı iletileri iletide, müşteri numarası gibi bazı uygulama tanımlı verileri tarafından birbirleriyle ilişkilidir.  
  
 Bağıntı kullanımda katılmak etkinlikleri bir <xref:System.ServiceModel.Activities.CorrelationHandle> Mesajlaşma etkinlikleri birbirine bağlamak için. Örneğin, bir <xref:System.ServiceModel.Activities.Send> bir hizmet ve bir sonraki çağırmak için kullanılan <xref:System.ServiceModel.Activities.Receive> hizmetinden bir geri alma, aynı paylaşmak için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle>. Bağıntı göre içeriği protokol tabanlı olup, bu temel düzeni kullanılır. Bağıntı tanıtıcı açıkça her etkinlik üzerinde ayarlanabilir veya etkinlikleri içinde bulunan bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik. Etkinlikler içinde yer alan bir <xref:System.ServiceModel.Activities.CorrelationScope> sahip tarafından yönetilen kendi bağıntı tanıtıcıları <xref:System.ServiceModel.Activities.CorrelationScope> ve gerektirmez <xref:System.ServiceModel.Activities.CorrelationHandle> açıkça ayarlamak için. A <xref:System.ServiceModel.Activities.CorrelationScope> kapsamını sağlar <xref:System.ServiceModel.Activities.CorrelationHandle> yönetimi için bir istek-yanıt bağıntısı ve ek bağıntı tür. İş akışı hizmetleri kullanarak barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> aynı varsayılan bağıntı yönetim olarak sahip <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik. Bu varsayılan bağıntı Yönetimi genellikle Mesajlaşma etkinlikleriyle içinde birçok senaryoda anlamına bir <xref:System.ServiceModel.Activities.CorrelationScope> ya da bir iş akışı hizmeti gerektirmez kendi <xref:System.ServiceModel.Activities.CorrelationHandle> birden çok Mesajlaşma etkinlikleri paralel veya iki gibi çakışma olmadığı sürece ayarlama <xref:System.ServiceModel.Activities.Receive> Aktiviteler paralel ya da iki <xref:System.ServiceModel.Activities.Send> etkinlikleri iki tarafından izlenen <xref:System.ServiceModel.Activities.Receive> etkinlikler. Bağıntı belirli her tür kapsayan bu bölümdeki konular, varsayılan bağıntı hakkında daha fazla bilgi sağlanmaktadır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Mesajlaşma etkinlikleri bkz [Mesajlaşma etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md) ve [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md).  
  
## <a name="protocol-based-correlation"></a>Protokol tabanlı bağıntı  
 Protokol tabanlı bağıntı aktarım mekanizması birbirine ve uygun örneğini iletilerini ilişkilendirmek için kullanır. Bazı sistem tarafından sağlanan Protokolü bağıntıları istek-yanıt bağıntısı ve bağlam tabanlı bağıntı içerir. İstek-yanıt bağıntısı gibi iki yönlü bir işlem oluşturmak için Mesajlaşma etkinlikleri tek bir çift ilişkilendirmek için kullanılan bir <xref:System.ServiceModel.Activities.Send> ile eşleştirilmiş bir <xref:System.ServiceModel.Activities.ReceiveReply>, veya bir <xref:System.ServiceModel.Activities.Receive> ile eşleştirilmiş bir <xref:System.ServiceModel.Activities.SendReply>. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] İş akışı Tasarımcısı bu deseni hızlıca uygulamak için etkinlik şablonları kümesi de sağlar. Bağlam tabanlı bağıntı açıklanan bağlam değişimi mekanizması dayalı [.NET bağlam değişimi protokolü belirtimi](http://go.microsoft.com/fwlink/?LinkID=166059). Bir bağlam tabanlı gibi bağlama bağlamına dayalı bağıntı kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> veya <xref:System.ServiceModel.NetTcpContextBinding> noktadaki kullanılması gerekir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]protokol bağıntı bkz [bağlam değişimi](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md), [dayanıklı çift yönlü](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md), ve [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] iş akışı Tasarımcısı etkinlik şablonları için bkz: [Mesajlaşma etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md). Örnek kod için bkz: [dayanıklı çift yönlü &#91; WF örnekleri &#93; ](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md) ve [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) örnekleri.  
  
## <a name="content-based-correlation"></a>İçeriğe dayalı bağıntı  
 İçeriğe dayalı bağıntı bazı bilgi parçasını iletide belirli bir örneğine ilişkilendirmek için kullanır. Protokol tabanlı bağıntı farklı olarak, içerik tabanlı bağıntı ilgili her iletide bu verileri bulunabileceği açıkça durumuna uygulama yazarı gerektirir. İçeriğe dayalı bağıntı kullanan etkinlikleri kullanarak bu ileti verileri belirtirseniz bir <xref:System.ServiceModel.MessageQuerySet>. İçeriğe dayalı bağıntı, bağlam bağlamaları gibi birini kullanmayın Hizmetleri ile iletişim kurarken yararlıdır <xref:System.ServiceModel.BasicHttpContextBinding>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]içeriğe dayalı bağıntı bkz [içerik tabanlı](../../../../docs/framework/wcf/feature-details/content-based-correlation.md). Örnek kod için bkz: [içerik tabanlı bağıntı](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md) ve [bağıntılı hesaplayıcı](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) örnekleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İçeriğe dayalı bağıntı](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [Bağıntılı hesaplayıcısı](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)  
 [Dayanıklı çift yönlü &#91; WF örnekleri &#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)  
 [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)
