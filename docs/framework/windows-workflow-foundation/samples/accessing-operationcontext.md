---
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 5a2731c7918c216221b0adcafd5c804e80f36dfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182854"
---
# <a name="accessing-operationcontext"></a>OperationContext Erişimi
Bu örnek, ileti etkinliklerinin<xref:System.ServiceModel.Activities.Receive> (ve) <xref:System.ServiceModel.Activities.Send>giden veya gelen bir <xref:System.ServiceModel.OperationContext.Current%2A> ileti içinde özel bir ileti üstbilgisine erişmek ve eklemek veya almak için özel bir kapsam etkinliğiyle nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma Etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, ileti etkinliklerinde erişim<xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> <xref:System.ServiceModel.OperationContext.Current%2A>için genişletilebilirlik noktalarının () nasıl kullanılacağını gösterir. Geri aramalar, yürütme üzerine ileti etkinlikleri tarafından <xref:System.Activities.IExecutionProperty> alınan bir uygulama olarak iş akışı çalışma süresi içinde kaydedilir. Bu <xref:System.Activities.IExecutionProperty> uygulamayla aynı kapsamdaki tüm ileti etkinlikleri etkilenir. Özellikle, bu örnek geri arama davranışını zorlamak için özel bir kapsam etkinliği kullanır. İstemci <xref:System.ServiceModel.Activities.ISendMessageCallback> iş akışında iş akışının giden <xref:System.Activities.WorkflowApplication.Id%2A> <xref:System.ServiceModel.Channels.MessageHeader>olarak kullanılmasını da içeren bir iş akışı kullanılır. Bu üstbilgi daha sonra hizmette <xref:System.ServiceModel.Activities.IReceiveMessageCallback> toplanır ve üstbilginin değeri konsola yazdırılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmetini ortaya çıkarır. Bu örneği çalıştırmak için, uygun URL ALA'ları eklenmelidir (ayrıntılar için [HTTP ve HTTPS yapılandırmaya](../../wcf/feature-details/configuring-http-and-https.md) bakınız), Visual Studio'yu Yönetici olarak çalıştırarak veya uygun ALA'ları eklemek için yükseltilmiş bir komut istemiyle aşağıdaki komutu çalıştırarak. Etki Alanınızın ve Kullanıcı Adınızın değiştirilip değiştirilediğinden emin olun.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ALA'ları eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü derleyin.  
  
    2. Çözüme sağ tıklayarak ve **Başlangıç Projeleri Ayarla'yı**seçerek birden çok başlangıç projesi ayarlayın.  
  
    3. **Hizmet** ve **İstemciyi** (bu sırada) birden çok başlangıç projesi olarak ekleyin.  
  
    4. Uygulamayı çalıştırın. İstemci konsolu iki kez çalışan bir iş akışını ve Hizmet penceresi bu iş akışlarının örnek kimliğini gösterir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
