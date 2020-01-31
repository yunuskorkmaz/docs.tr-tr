---
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: ae0615c8cf2fa33f3bb363f77c0d06440b6afc13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743713"
---
# <a name="hello-world-with-the-routing-service"></a>Yönlendirme Hizmeti ile Merhaba Dünya
Bu örnek Windows Communication Foundation (WCF) yönlendirme hizmetini gösterir. Yönlendirme hizmeti, uygulamanıza içerik tabanlı bir yönlendirici eklenmesini kolaylaştıran bir WCF bileşenidir. Bu örnek, yönlendirme hizmetini kullanarak iletişim kurmak için standart WCF Hesaplayıcı örneğine uyum sağlar. Bu örnekte, hesap makinesi istemcisi, yönlendirici tarafından kullanıma sunulan bir uç noktaya ileti gönderecek şekilde yapılandırılmıştır. Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmek ve hesap makinesi hizmetine karşılık gelen bir uç noktaya iletmek üzere yapılandırılmıştır. Böylece istemciden gönderilen iletiler, yönlendirici tarafından alınır ve gerçek Hesaplayıcı hizmetine yeniden yönlendirilir. Hesaplayıcı hizmetinden gelen iletiler yönlendiriciye geri gönderilir, bu da yeniden Hesaplayıcı istemcisine geçirilir.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak, HelloRoutingService. sln ' yi açın.

2. F5 veya CTRL + SHIFT + B tuşlarına basın.

    > [!NOTE]
    > F5 tuşuna basarsanız, hesap makinesi Istemcisi otomatik olarak başlatılır. CTRL + SHIFT + B 'ye (derleme) basarsanız, aşağıdaki uygulamaları kendiniz başlatmanız gerekir.
    >
    > 1. Hesaplayıcı istemcisi (./CalculatorClient/bin/client.exe
    > 2. Hesaplayıcı hizmeti (./CalculatorService/bin/service.exe)
    > 3. Yönlendirme hizmeti (./RoutingService/bin/RoutingService.exe)

3. İstemcisini başlatmak için ENTER tuşuna basın.

     Aşağıdaki çıktıyı görmeniz gerekir:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Code veya App. config aracılığıyla yapılandırılabilir
 Örnek, yönlendirici davranışını tanımlamak için bir App. config dosyası kullanmak üzere yapılandırılmıştır. Ayrıca, App. config dosyasının adını başka bir şeye değiştirerek, tanınmayacak ve ConfigureRouterViaCode () yöntemi çağrısının açıklamasını Açıklama eklemek için de kullanabilirsiniz. Her iki yöntem de yönlendiriciden aynı davranışa neden olur.

### <a name="scenario"></a>Senaryo
 Bu örnek, bir temel ileti göndericisi görevi gören yönlendiriciyi gösterir. Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktası kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü işlevi görür.

### <a name="real-world-scenario"></a>Gerçek dünya senaryosu
 Contoso, hizmetlerinin adlandırma, adresleme, yapılandırma ve güvenliğine sahip olduğu esnekliği artırmak istiyor. Bunu yapmak için, genel kullanıma yönelik bir uç nokta olarak görev yapmak üzere hizmetlerinin önüne temel bir ileti göndericisi yerleştirirler. Bu, gerçek hizmetlerinin önüne ek güvenlik yerleştirmelerini ve daha sonra ölçeklendirilebilir çözüm veya hizmet sürümü oluşturmayı daha kolay hale getirir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
