---
title: OperationContext erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: cefbc3b10114b427518e640809462eedb131d695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-operationcontext"></a>OperationContext erişimi
Bu örnek gösterilmektedir nasıl Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send>) özel kapsam etkinliği ile erişmek için kullanılan <xref:System.ServiceModel.OperationContext.Current%2A> ve ekleyebilir veya bir özel ileti üstbilgisi içinde bir giden veya gelen ileti alma.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek genişletilebilirlik noktaları kullanmayı gösterir (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) erişmek için Mesajlaşma etkinlikleriyle <xref:System.ServiceModel.OperationContext.Current%2A>. Geri aramalar içinde iş akışı çalışma zamanı uygulaması kaydedilen <xref:System.Activities.IExecutionProperty> , toplanma yürütme sırasında Mesajlaşma etkinlikleri tarafından. Herhangi bir Mesajlaşma etkinlik olarak aynı kapsamda <xref:System.Activities.IExecutionProperty> uygulama etkilenir. Özellikle, bu örnek geri çağırma davranışına zorlamak için bir özel kapsam aktivitesi kullanır. <xref:System.ServiceModel.Activities.ISendMessageCallback> İstemci iş akışı içinde iş akışının dahil etmek için kullanılan <xref:System.Activities.WorkflowApplication.Id%2A> giden olarak <xref:System.ServiceModel.Channels.MessageHeader>. Bu üst sonra hizmetini kullanarak kayıt <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve konsola yazdırılır üstbilgi değeri.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmeti kullanıma sunar. Bu örnek, uygun URL ACL çalıştırmak için eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio Yönetici olarak çalıştırarak veya uygun ACL'ler eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu çalıştırarak. Etki alanı ve kullanıcı adı yerine emin olun.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  URL ACL eklendikten sonra aşağıdaki adımları kullanın.  
  
    1.  Çözümü oluşturun.  
  
    2.  Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**.  
  
    3.  Ekleme **hizmet** ve **istemci** (sırayla) birden fazla başlangıç projesi olarak.  
  
    4.  Uygulamayı çalıştırın. İstemci Konsolu iki kez çalışan bir iş akışındaki gösterir ve bu iş akışlarının örnek kimliği hizmet penceresi gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
