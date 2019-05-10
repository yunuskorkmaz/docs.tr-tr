---
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: fc3be627c8dfc8d8e49fde01684968a54912f548
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617331"
---
# <a name="accessing-operationcontext"></a>OperationContext Erişimi
Bu örnek gösterir nasıl Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send>) bir özel kapsam etkinliğiyle erişmek için kullanılan <xref:System.ServiceModel.OperationContext.Current%2A> ve ekleyebilir veya bir giden veya gelen ileti içinde bir özel ileti üst bilgisi alınamıyor.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek genişletilebilirlik noktaları kullanmayı gösterir (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) erişmek için Mesajlaşma etkinlikleriyle <xref:System.ServiceModel.OperationContext.Current%2A>. Geri çağırmaları uygulaması iş akışı çalışma zamanı içinde kayıtlı <xref:System.Activities.IExecutionProperty> , alındığından yürütme sırasında Mesajlaşma etkinlikleri tarafından. Herhangi bir Mesajlaşma etkinlik, aynı kapsamda <xref:System.Activities.IExecutionProperty> uygulama etkilenir. Özellikle bu örnek, geri çağırma davranışı zorlamak için bir özel kapsam etkinliği kullanır. <xref:System.ServiceModel.Activities.ISendMessageCallback> İş akışının eklemek için istemci iş akışı içinde kullanılan <xref:System.Activities.WorkflowApplication.Id%2A> giden olarak <xref:System.ServiceModel.Channels.MessageHeader>. Bu üstbilginin ardından hizmetini kullanarak devralındığında <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve konsola yazdırılır üstbilgisinin değeri.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Bu örnek, bir iş akışı hizmeti kullanarak HTTP uç noktalarını kullanıma sunar. Bu örnek, uygun URL ACL çalıştırılacak eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio'yu yönetici olarak çalıştırdığınızdan veya uygun ACL'lerin eklemek için aşağıdaki komutu yükseltilmiş bir isteminde yürütülüyor. Kullanıcı adı ve etki alanı başvurulduğunda emin olun.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ACL eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü oluşturun.  
  
    2. Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**.  
  
    3. Ekleme **hizmet** ve **istemci** (bu sırayla) birden çok başlangıç projesi olarak.  
  
    4. Uygulamayı çalıştırın. İstemci Konsolu iki kez çalışan bir iş akışı gösterir ve bu iş akışı örnek kimliği hizmet verme penceresi gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
