---
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 83f3a6cacd3ee86050f65a886d446ab8da7d3690
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094715"
---
# <a name="accessing-operationcontext"></a>OperationContext Erişimi
Bu örnek, ileti etkinliklerinin (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send>) bir özel kapsam etkinliğiyle birlikte <xref:System.ServiceModel.OperationContext.Current%2A> erişmek ve giden veya gelen bir ileti içinde özel bir ileti üstbilgisi eklemek veya almak için nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback><xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, <xref:System.ServiceModel.OperationContext.Current%2A>erişmek için mesajlaşma etkinliklerinde genişletilebilirlik noktalarının (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) nasıl kullanılacağını gösterir. Geri çağrılar, yürütme sonrasında mesajlaşma etkinlikleri tarafından oluşturulan <xref:System.Activities.IExecutionProperty> bir uygulama olarak iş akışı çalışma zamanı içinde kaydedilir. <xref:System.Activities.IExecutionProperty> uygulamayla aynı kapsamdaki tüm mesajlaşma etkinlikleri etkilenir. Özellikle bu örnek, geri çağırma davranışını zorlamak için özel bir kapsam etkinliği kullanır. <xref:System.ServiceModel.Activities.ISendMessageCallback>, istemci iş akışında, iş akışının <xref:System.Activities.WorkflowApplication.Id%2A> giden <xref:System.ServiceModel.Channels.MessageHeader>olarak eklenmesi için kullanılır. Bu üst bilgi daha sonra <xref:System.ServiceModel.Activities.IReceiveMessageCallback> kullanılarak hizmette alınır ve üstbilginin değeri konsola yazdırılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar. Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek. Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.  
  
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
