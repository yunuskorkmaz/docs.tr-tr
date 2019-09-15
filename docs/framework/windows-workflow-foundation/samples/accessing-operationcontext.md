---
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: dea990e275125dc1cd2255b88e506d363c3ac78e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989385"
---
# <a name="accessing-operationcontext"></a>OperationContext Erişimi
Bu örnek, ileti etkinliklerinin (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send>) giden veya gelen bir ileti içinde özel bir ileti başlığına erişmek <xref:System.ServiceModel.OperationContext.Current%2A> ve bunları eklemek veya almak için özel bir kapsam etkinliğiyle nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, erişim<xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.OperationContext.Current%2A>için mesajlaşma etkinliklerinde genişletilebilirlik noktalarının <xref:System.ServiceModel.Activities.IReceiveMessageCallback>()) nasıl kullanılacağını gösterir. Geri çağrılar, yürütme sonrasında mesajlaşma etkinlikleri tarafından <xref:System.Activities.IExecutionProperty> oluşturulan bir uygulama olarak iş akışı çalışma zamanı içinde kaydedilir. Bu <xref:System.Activities.IExecutionProperty> uygulamayla aynı kapsamdaki tüm mesajlaşma etkinlikleri etkilenir. Özellikle bu örnek, geri çağırma davranışını zorlamak için özel bir kapsam etkinliği kullanır. , <xref:System.ServiceModel.Activities.ISendMessageCallback> İstemci iş akışında, <xref:System.Activities.WorkflowApplication.Id%2A> iş akışını giden bir giden <xref:System.ServiceModel.Channels.MessageHeader>olarak dahil etmek için kullanılır. Bu üst bilgi daha sonra hizmetinde kullanılarak <xref:System.ServiceModel.Activities.IReceiveMessageCallback> alınır ve üst bilgi değeri konsola yazdırılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar. Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](https://go.microsoft.com/fwlink/?LinkId=70353) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek. Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü oluşturun.  
  
    2. Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın.  
  
    3. **Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.  
  
    4. Uygulamayı çalıştırın. İstemci konsolunda, iki kez çalışan bir iş akışı gösterilir ve hizmet penceresinde bu iş akışlarının örnek KIMLIĞI gösterilir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
