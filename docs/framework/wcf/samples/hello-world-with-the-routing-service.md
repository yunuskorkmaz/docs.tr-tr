---
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 490d91da22b11c269c4d3c11d376087919a608e0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519205"
---
# <a name="hello-world-with-the-routing-service"></a>Yönlendirme Hizmeti ile Merhaba Dünya
Bu örnek, Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir. Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir. Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar. Bu örnekte, hesaplayıcı istemci yönlendirici tarafından sunulan bir uç noktaya iletileri göndermek için yapılandırılır. Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmesini ve hesaplayıcı hizmetine karşılık gelen bir uç nokta iletmek için yapılandırılır. Bu nedenle istemci tarafından gönderilen iletileri yönlendirici tarafından alınan ve gerçek hesaplayıcı hizmete yeniden yönlendirilen. Hesaplayıcı hizmetinden gelen iletileri hangi sırayla bunları hesaplayıcı istemciye aktarır yeniden yönlendiriciye gönderilir.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], HelloRoutingService.sln açın.  
  
2.  F5 veya CTRL + SHIFT + B tuşlarına basın.  
  
    > [!NOTE]
    >  F5 tuşuna basarsanız, hesaplayıcı istemci otomatik olarak başlar. CTRL + SHIFT + B (derleme) tuşuna basarsanız, kendiniz uygulamaları başlatmanız gerekir.  
    >  
    > 1.  Hesaplayıcı istemci (./CalculatorClient/bin/client.exe  
    > 2.  Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)  
    > 3.  Yönlendirme Hizmeti (. / RoutingService/bin/RoutingService.exe)  
  
3.  İstemcisini başlatmak için ENTER tuşuna basın.  
  
     Aşağıdaki çıktıyı görmeniz gerekir:  
  
     Add(100,15.99) 115.99 =  
  
     Subtract(145,76.54) 68.46 =  
  
     Multiply(9,81.25) 731.25 =  
  
     Divide(22,7) 3.14285714285714 =  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod veya App.Config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca, App.config dosyasının adı bir şeye tanınmıyor şekilde değiştirin ve ConfigureRouterViaCode() yöntem çağrısına açıklamasını kaldırın. Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek, bir temel ileti pompası davranan yönlendirici gösterir. Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktaları kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü olarak görev yapar.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso adlandırma, adres, yapılandırma ve güvenlik hizmetleri olan esnekliği artırmak istiyor. Bunu yapmak için bunlar bir temel ileti pompası genel kullanıma yönelik bir uç nokta yapması hizmetlerini önüne koyun. Bu ek güvenlik gerçek hizmetlerini önüne yerleştirin ve uygulamak daha sonraki bir tarihte daraltılmasına çözümleri veya hizmet sürümü oluşturma kolaylaştırmak sağlar.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
