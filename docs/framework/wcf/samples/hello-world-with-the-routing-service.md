---
title: "Yönlendirme Hizmeti ile Merhaba Dünya"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ba910afe91af07ecbdb2c71bba2fa496c52f2f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="hello-world-with-the-routing-service"></a>Yönlendirme Hizmeti ile Merhaba Dünya
Bu örnek gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti. Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni. Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hesaplayıcı yönlendirme hizmeti kullanarak iletişim kurmak için örnek. Bu örnekte, hesaplayıcı istemci yönlendirici tarafından kullanıma sunulan bir uç nokta ileti göndermek için yapılandırılır. Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmek ve hesaplayıcı hizmeti karşılık gelen bir uç nokta iletmek için yapılandırılır. Bu nedenle istemci tarafından gönderilen iletileri yönlendirici tarafından alınan ve gerçek hesaplayıcı hizmete yeniden yönlendirildi. Hesaplayıcı hizmetinden gelen iletileri hangi sırayla bunları hesaplayıcı istemciye aktarır geri yönlendiriciye gönderilir.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], HelloRoutingService.sln açın.  
  
2.  F5 veya CTRL + SHIFT + B tuşuna basın.  
  
    > [!NOTE]
    >  F5 tuşuna basarsanız hesaplayıcı istemci otomatik olarak başlar. CTRL + SHIFT + B (yapı) tuşuna basarsanız, uygulamaları kendiniz başlamalıdır.  
    >   
    >  1.  Hesaplayıcı istemci (./CalculatorClient/bin/client.exe  
    > 2.  Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)  
    > 3.  Yönlendirme Hizmeti (. / RoutingService/bin/RoutingService.exe)  
  
3.  İstemcisini başlatmak için ENTER tuşuna basın.  
  
     Şu çıktı görmeniz gerekir:  
  
     Add(100,15.99) 115.99 =  
  
     Subtract(145,76.54) 68.46 =  
  
     Multiply(9,81.25) 731.25 =  
  
     Divide(22,7) 3.14285714285714 =  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod ya da App.Config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca, App.config dosyasının adı başka bir şey için tanınmıyor şekilde değiştirin ve ConfigureRouterViaCode() yöntemi çağrısına açıklamadan çıkarın. Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek, temel ileti Pompalama işlev gören yönlendirici gösterir. Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktaları kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü olarak görev yapar.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso adlandırma, adresleme, yapılandırma ve hizmetlerinin güvenliğini sahip esnekliğini artırmak ister. Bunu yapmak için temel ileti Pompalama genel kullanıma yönelik bir uç nokta davranacak şekilde hizmetlerini önüne yerleştirin. Bu ek güvenlik gerçek hizmetlerini önüne yerleştirin ve uygulamak çözümleri veya hizmet sürümü oluşturma daha sonraki bir tarihte ölçeklendirilmiş kolaylaştırmak sağlar.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
