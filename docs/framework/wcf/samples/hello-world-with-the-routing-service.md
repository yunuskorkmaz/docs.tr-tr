---
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183640"
---
# <a name="hello-world-with-the-routing-service"></a>Yönlendirme Hizmeti ile Merhaba Dünya
Bu örnek, Windows Communication Foundation (WCF) Yönlendirme Hizmetini göstermektedir. Yönlendirme Hizmeti, uygulamanıza içerik tabanlı bir yönlendirici eklemeyi kolaylaştıran bir WCF bileşenidir. Bu örnek, Yönlendirme Hizmetini kullanarak iletişim kurmak için standart WCF Hesap Makinesi Örneğini uyarlar. Bu örnekte, Hesap Makinesi istemcisi yönlendirici tarafından açığa çıkarılan bir bitiş noktasına ileti gönderecek şekilde yapılandırılır. Yönlendirme Hizmeti, gönderilen tüm iletileri kabul etmek ve hesap makinesi hizmetine karşılık gelen bir bitiş noktasına iletmek için yapılandırılmıştır. Böylece istemciden gönderilen iletiler yönlendirici tarafından alınır ve gerçek Hesap Makinesi hizmetine yeniden yönlendirilir. Hesap Makinesi hizmetinden gelen iletiler yönlendiriciye geri gönderilir ve bu da onları Hesap Makinesi istemcisine geri gönderir.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012'yi kullanarak HelloRoutingService.sln'yi açın.

2. F5 veya CTRL+SHIFT+B tuşuna basın.

    > [!NOTE]
    > F5 tuşuna baslarsanız, Hesap Makinesi İstemci otomatik olarak başlar. CTRL+SHIFT+B (yapı) tuşuna basarsanız, uygulamaları kendiniz takip etmeye başlamalısınız.
    >
    > 1. Hesap makinesi istemcisi (./CalculatorClient/bin/client.exe
    > 2. Hesap makinesi hizmeti (./CalculatorService/bin/service.exe)
    > 3. Yönlendirme hizmeti (./RoutingService/bin/RoutingService.exe)

3. İstemciyi başlatmak için ENTER tuşuna basın.

     Aşağıdaki çıktıyı görmeniz gerekir:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Kod veya App.Config ile yapılandırılabilir
 Örnek gemiler, yönlendiricinin davranışını tanımlamak için bir App.config dosyası kullanacak şekilde yapılandırılmıştır. App.config dosyasının adını, tanınmaması ve YapılandırmaRouterViaCode() için yapılan yöntem çağrısının yorumsuz olması için başka bir şeyle de değiştirebilirsiniz. Her iki yöntem de yönlendiriciden aynı davranışla sonuçlanır.

### <a name="scenario"></a>Senaryo
 Bu örnek, yönlendiricinin temel bir mesaj pompası olarak hareket ettiğini gösterir. Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış hedef uç noktaları kümesine aktarmak üzere yapılandırılan saydam bir proxy düğümü görevi görür.

### <a name="real-world-scenario"></a>Gerçek Dünya Senaryosu
 Contoso, hizmetlerinin adlandırılması, ele alınması, yapılandırması ve güvenliği konusunda sahip olduğu esnekliği artırmak istiyor. Bunu yapmak için, bir kamu bakan bitiş noktası olarak hareket etmek için kendi hizmetlerinin önünde temel bir mesaj pompası yerleştirin. Bu, gerçek hizmetlerinin önüne ek güvenlik yerleştirmelerine ve daha sonraki bir tarihte ölçeklenmiş çözümleri veya hizmet sürümünü uygulamayı kolaylaştırır.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
