---
description: 'Hakkında daha fazla bilgi edinin: yönlendirme hizmeti ile Merhaba Dünya'
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 1741c7d1f1e474864d66220fd160633997744876
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631976"
---
# <a name="hello-world-with-the-routing-service"></a>Yönlendirme Hizmeti ile Merhaba Dünya

Bu örnek Windows Communication Foundation (WCF) yönlendirme hizmetini gösterir. Yönlendirme hizmeti, uygulamanıza içerik tabanlı bir yönlendirici eklenmesini kolaylaştıran bir WCF bileşenidir. Bu örnek, yönlendirme hizmetini kullanarak iletişim kurmak için standart WCF Hesaplayıcı örneğine uyum sağlar. Bu örnekte, hesap makinesi istemcisi, yönlendirici tarafından kullanıma sunulan bir uç noktaya ileti gönderecek şekilde yapılandırılmıştır. Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmek ve hesap makinesi hizmetine karşılık gelen bir uç noktaya iletmek üzere yapılandırılmıştır. Böylece istemciden gönderilen iletiler, yönlendirici tarafından alınır ve gerçek Hesaplayıcı hizmetine yeniden yönlendirilir. Hesaplayıcı hizmetinden gelen iletiler yönlendiriciye geri gönderilir, bu da yeniden Hesaplayıcı istemcisine geçirilir.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak, HelloRoutingService. sln ' yi açın.

2. F5 veya CTRL + SHIFT + B tuşlarına basın.

    > [!NOTE]
    > F5 tuşuna basarsanız, hesap makinesi Istemcisi otomatik olarak başlatılır. CTRL + SHIFT + B 'ye (derleme) basarsanız, aşağıdaki uygulamaları kendiniz başlatmanız gerekir.
    >
    > 1. Hesaplayıcı istemcisi (./Hesaplatorclient/bin/client.exe
    > 2. Hesaplayıcı hizmeti (./Hesaplayıcı Torservice/bin/service.exe)
    > 3. Yönlendirme hizmeti (./RoutingService/bin/RoutingService.exe)

3. İstemcisini başlatmak için ENTER tuşuna basın.

     Aşağıdaki çıkışı görmeniz gerekir:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Kod veya App.Config aracılığıyla yapılandırılabilir

 Örnek, yönlendirici davranışını tanımlamak için bir App.config dosyası kullanmak üzere yapılandırılmıştır. Ayrıca, App.config dosyanın adını başka bir şeye değiştirerek tanınmayacak ve ConfigureRouterViaCode () yöntem çağrısının açıklamasını belirleyebilmeniz gerekir. Her iki yöntem de yönlendiriciden aynı davranışa neden olur.

### <a name="scenario"></a>Senaryo

 Bu örnek, bir temel ileti göndericisi görevi gören yönlendiriciyi gösterir. Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktası kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü işlevi görür.

### <a name="real-world-scenario"></a>Gerçek dünya senaryosu

 Contoso, hizmetlerinin adlandırma, adresleme, yapılandırma ve güvenliğine sahip olduğu esnekliği artırmak istiyor. Bunu yapmak için, genel kullanıma yönelik bir uç nokta olarak görev yapmak üzere hizmetlerinin önüne temel bir ileti göndericisi yerleştirirler. Bu, gerçek hizmetlerinin önüne ek güvenlik yerleştirmelerini ve daha sonra ölçeklendirilebilir çözüm veya hizmet sürümü oluşturmayı daha kolay hale getirir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))
