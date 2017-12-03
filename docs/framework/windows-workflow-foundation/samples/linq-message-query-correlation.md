---
title: "LINQ ileti sorgu bağıntısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124f76012f342eff9b11a7208df1103cded3843c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="linq-message-query-correlation"></a>LINQ ileti sorgu bağıntısı
Bu örnek özel bir kullanılarak içerik tabanlı bağıntı bunu nasıl yapacağınızı gösterir <xref:System.ServiceModel.Dispatcher.MessageQuery> sistem tarafından sağlanan aksine uygulama <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, içerik tabanlı bağıntı.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, gelen genişletmek gösterilmiştir <xref:System.ServiceModel.Dispatcher.MessageQuery> bağıntı amaçları doğrultusunda temel sınıfı. Özel uygulama `LinqMessageQuery`, kullanıcıların XLinq kullanarak iletisi içinde bulmak için bir XName belirtmesini sağlar. Sorgu tarafından alınan veri uygun iş akışı örneği iletileri gönderme bağıntı anahtarı oluşturmak için kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmeti kullanıma sunar. Bu örnek, uygun URL ACL çalıştırmak için eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio Yönetici olarak çalıştırarak veya uygun ACL'ler eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu çalıştırarak. Etki alanı ve kullanıcı adı yerine emin olun.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  URL ACL eklendikten sonra aşağıdaki adımları kullanın.  
  
    1.  Çözümü oluşturun.  
  
    2.  Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**. Ekleme **hizmet** ve **istemci** (sırayla) birden fazla başlangıç projesi olarak.  
  
    3.  Uygulamayı çalıştırın. İstemci konsolunu bir sipariş göndermek, satın alma siparişi kimliği alma ve daha sonra sipariş onayı iş akışı gösterilmektedir. Hizmet verme penceresi işlenmekte olan istek gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
