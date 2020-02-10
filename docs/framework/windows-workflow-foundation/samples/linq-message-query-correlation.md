---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cd91a171f3242cfd7e8ac0404e24ac065919bcce
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094624"
---
# <a name="linq-message-query-correlation"></a>LINQ İleti Kuyruğu Bağıntısı
Bu örnek, sistem tarafından sağlanmış <xref:System.ServiceModel.XPathMessageQuery>aksine özel bir <xref:System.ServiceModel.Dispatcher.MessageQuery> uygulamasını kullanarak içerik tabanlı bağıntı oluşturmayı gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, Içerik tabanlı bağıntı.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, bağıntı amaçları doğrultusunda <xref:System.ServiceModel.Dispatcher.MessageQuery> temel sınıftan genişletmeyi gösterir. `LinqMessageQuery`özel uygulama, kullanıcıların Xlınq kullanarak ileti içinde bulmak için bir XName sağlamasına izin verir. Sorgu tarafından alınan veriler, uygun iş akışı örneğine ileti göndermek için bağıntı anahtarını oluşturmak üzere kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar. Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek. Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
