---
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: b8a09aff7b5a30b5267fbdbd7bd6391996f359c7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715096"
---
# <a name="accessing-operationcontext"></a>OperationContext Erişimi
Bu örnek, ileti etkinliklerinin (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send>) bir özel kapsam etkinliğiyle birlikte <xref:System.ServiceModel.OperationContext.Current%2A> erişmek ve giden veya gelen bir ileti içinde özel bir ileti üstbilgisi eklemek veya almak için nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösterir  
 Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback><xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, <xref:System.ServiceModel.OperationContext.Current%2A>erişmek için mesajlaşma etkinliklerinde genişletilebilirlik noktalarının (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) nasıl kullanılacağını gösterir. Geri çağrılar, yürütme sonrasında mesajlaşma etkinlikleri tarafından oluşturulan <xref:System.Activities.IExecutionProperty> bir uygulama olarak iş akışı çalışma zamanı içinde kaydedilir. <xref:System.Activities.IExecutionProperty> uygulamayla aynı kapsamdaki tüm mesajlaşma etkinlikleri etkilenir. Özellikle bu örnek, geri çağırma davranışını zorlamak için özel bir kapsam etkinliği kullanır. <xref:System.ServiceModel.Activities.ISendMessageCallback>, istemci iş akışında, iş akışının <xref:System.Activities.WorkflowApplication.Id%2A> giden <xref:System.ServiceModel.Channels.MessageHeader>olarak eklenmesi için kullanılır. Bu üst bilgi daha sonra <xref:System.ServiceModel.Activities.IReceiveMessageCallback> kullanılarak hizmette alınır ve üstbilginin değeri konsola yazdırılır.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
