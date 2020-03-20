---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182799"
---
# <a name="linq-message-query-correlation"></a>LINQ İleti Kuyruğu Bağıntısı
Bu örnek, sistem tarafından sağlanan <xref:System.ServiceModel.Dispatcher.MessageQuery> <xref:System.ServiceModel.XPathMessageQuery>ın aksine özel bir uygulama kullanarak içerik tabanlı korelasyonun nasıl yapılacağını göstermektedir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, Içerik Tabanlı Korelasyon.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, korelasyon <xref:System.ServiceModel.Dispatcher.MessageQuery> amacıyla taban sınıftan nasıl genişletilecektir gösterir. Özel uygulama, `LinqMessageQuery`, kullanıcıların XLinq kullanarak mesaj içinde bulmak için bir XName sağlamak için izin verir. Sorgu tarafından alınan veriler, iletileri uygun iş akışı örneğine göndermek için korelasyon anahtarını oluşturmak için kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmetini ortaya çıkarır. Bu örneği çalıştırmak için, uygun URL ALA'ları eklenmelidir (ayrıntılar için [HTTP ve HTTPS yapılandırmaya](../../wcf/feature-details/configuring-http-and-https.md) bakınız), Visual Studio'yu Yönetici olarak çalıştırarak veya uygun ALA'ları eklemek için yükseltilmiş bir komut istemiyle aşağıdaki komutu çalıştırarak. Etki Alanınızın ve Kullanıcı Adınızın değiştirilip değiştirilediğinden emin olun.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. URL ALA'ları eklendikten sonra aşağıdaki adımları kullanın.  
  
    1. Çözümü derleyin.  
  
    2. Çözüme sağ tıklayarak ve **Başlangıç Projeleri Ayarla'yı**seçerek birden çok başlangıç projesi ayarlayın. **Hizmet** ve **İstemciyi** (bu sırada) birden çok başlangıç projesi olarak ekleyin.  
  
    3. Uygulamayı çalıştırın. İstemci konsolu, sipariş gönderen ve satınalma siparişidini alan ve daha sonra siparişi onaylayan bir iş akışı gösterir. Hizmet penceresi, işlenen istekleri gösterir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
