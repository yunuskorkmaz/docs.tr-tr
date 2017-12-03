---
title: "Zaman Uyumsuz Bulma Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 229e2ff6e630527e3735e3c48f698f582b0b60f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-find-sample"></a>Zaman Uyumsuz Bulma Örneği
Bu örnek, bir istemci uygulaması zaman uyumsuz bulma işlemi kullanmayı gösterir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu tasarım deseni aşağıdaki avantajı, istemci bulma isteği sonucunda bulunan uç noktaları zaman uyumsuz olarak bildirilir ' dir. Bunun nasıl çalıştığını görmek için Client.cs dosyasını açın. Not <xref:System.ServiceModel.Discovery.DiscoveryClient> nesnesi iki temsilciler olayı olarak işleyicilerinin sahiptir. Bir temsilci çağrılır bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> olayı oluşturulur ve her zaman başka adlı bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayı oluşturulur. Örnek nasıl uygulamanızda bu deseni kullanabilir gösterir.  
  
> [!NOTE]
>  Bu örnek HTTP uç noktaları kullanır ve çalıştırmak için doğru URL ACL eklenmesi gerekir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HTTP ve HTTPS yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir. Komut olduğu gibi çalışmazsa şu bağımsız değişkenleri için kullanıcı adı ve etki alanı yerine isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AsyncFind.sln açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi ve \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug veya \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug dizinine gidin ve Service.exe çalıştırın.  
  
4.  Hizmeti başlatıldıktan sonra \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug ya da WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug dizine gidin ve Client.exe çalıştırın.  
  
5.  İstemci bulun ve hizmeti çağırmak mümkün gözlemleyin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Ayrıca Bkz.
