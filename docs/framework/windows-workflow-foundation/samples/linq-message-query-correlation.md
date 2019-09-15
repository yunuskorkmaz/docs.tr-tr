---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 202d65914d32245952f308d3115ec93231f95f15
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989333"
---
# <a name="linq-message-query-correlation"></a>LINQ İleti Kuyruğu Bağıntısı
Bu örnek, sistem tarafından sağlanın <xref:System.ServiceModel.Dispatcher.MessageQuery> <xref:System.ServiceModel.XPathMessageQuery>aksine özel bir uygulama kullanarak içerik tabanlı bağıntı oluşturmayı gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, içerik tabanlı bağıntı.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, bağıntı amaçları doğrultusunda <xref:System.ServiceModel.Dispatcher.MessageQuery> temel sınıftan genişletmeyi gösterir. Özel uygulama `LinqMessageQuery`, kullanıcıların xlınq kullanarak ileti içinde bulmak için bir XName sağlamasına izin verir. Sorgu tarafından alınan veriler, uygun iş akışı örneğine ileti göndermek için bağıntı anahtarını oluşturmak üzere kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar. Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](https://go.microsoft.com/fwlink/?LinkId=70353) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek. Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü oluşturun.  
  
    2. Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın. **Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.  
  
    3. Uygulamayı çalıştırın. İstemci konsolu sipariş gönderen ve satın alma siparişi kimliğini alan ve ardından siparişi onaylayan bir iş akışını gösterir. Hizmet penceresinde işlenmekte olan istekler gösterilir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
