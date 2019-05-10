---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 5e979e6539d94d15b74f1da14f7082431ed2ff8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622722"
---
# <a name="linq-message-query-correlation"></a>LINQ İleti Kuyruğu Bağıntısı
Bu örnek özel bir kullanarak içerik temelli bağıntı yapmak nasıl gösterir <xref:System.ServiceModel.Dispatcher.MessageQuery> aksine, sistem tarafından sağlanan uygulama <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, içerik temelli bağıntı.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek nasıl gelen genişletileceğini gösterir <xref:System.ServiceModel.Dispatcher.MessageQuery> bağıntı amaçları için temel sınıf. Özel uygulama `LinqMessageQuery`, XLinq kullanarak ileti içinde bulunacak bir XName sağlamak kullanıcıların sağlar. Sorgu tarafından alınan verileri, uygun iş akışı örneği iletileri gönderme bağıntı anahtar oluşturmak için kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Bu örnek, bir iş akışı hizmeti kullanarak HTTP uç noktalarını kullanıma sunar. Bu örnek, uygun URL ACL çalıştırılacak eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio'yu yönetici olarak çalıştırdığınızdan veya uygun ACL'lerin eklemek için aşağıdaki komutu yükseltilmiş bir isteminde yürütülüyor. Kullanıcı adı ve etki alanı başvurulduğunda emin olun.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ACL eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü oluşturun.  
  
    2. Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**. Ekleme **hizmet** ve **istemci** (bu sırayla) birden çok başlangıç projesi olarak.  
  
    3. Uygulamayı çalıştırın. İstemci konsolu bir sipariş göndermeden, Sipariş No alma ve daha sonra siparişi onaylayan bir iş akışı gösterilmektedir. Hizmet verme penceresi işlenmekte olan istek gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
