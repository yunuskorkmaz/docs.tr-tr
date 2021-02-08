---
description: "Daha fazla bilgi edinin: OperationContext 'e erişme"
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 768475f115f653630aaedeee976d0c96bc9e4dd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792628"
---
# <a name="accessing-operationcontext"></a>OperationContext Erişimi

Bu örnek, ileti etkinliklerinin ( <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send> ) <xref:System.ServiceModel.OperationContext.Current%2A> giden veya gelen bir ileti içinde özel bir ileti başlığına erişmek ve bunları eklemek veya almak için özel bir kapsam etkinliğiyle nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  

 Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback> , <xref:System.ServiceModel.Activities.IReceiveMessageCallback> .  
  
## <a name="discussion"></a>Tartışma  

 Bu örnek <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> , erişim için mesajlaşma etkinliklerinde genişletilebilirlik noktalarının ()) nasıl kullanılacağını gösterir <xref:System.ServiceModel.OperationContext.Current%2A> . Geri çağrılar, <xref:System.Activities.IExecutionProperty> yürütme sonrasında mesajlaşma etkinlikleri tarafından oluşturulan bir uygulama olarak iş akışı çalışma zamanı içinde kaydedilir. Bu uygulamayla aynı kapsamdaki tüm mesajlaşma etkinlikleri <xref:System.Activities.IExecutionProperty> etkilenir. Özellikle bu örnek, geri çağırma davranışını zorlamak için özel bir kapsam etkinliği kullanır. , <xref:System.ServiceModel.Activities.ISendMessageCallback> İstemci iş akışında, iş akışını <xref:System.Activities.WorkflowApplication.Id%2A> giden bir giden olarak dahil etmek için kullanılır <xref:System.ServiceModel.Channels.MessageHeader> . Bu üst bilgi daha sonra hizmetinde kullanılarak alınır <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve üst bilgi değeri konsola yazdırılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar. Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek. Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü derleyin.  
  
    2. Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın.  
  
    3. **Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.  
  
    4. Uygulamayı çalıştırın. İstemci konsolunda, iki kez çalışan bir iş akışı gösterilir ve hizmet penceresinde bu iş akışlarının örnek KIMLIĞI gösterilir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
