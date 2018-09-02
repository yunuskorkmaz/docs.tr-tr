---
title: Zaman Uyumsuz Bulma Örneği
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: 37edcb4d1f04eb56d3f24ca3acc3543d7f9696f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424397"
---
# <a name="asynchronous-find-sample"></a>Zaman Uyumsuz Bulma Örneği
Bu örnek, bir istemci uygulamasında zaman uyumsuz bulma işlemi işlemi gösterilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu tasarım deseni aşağıdaki istemci bulma isteği sonucunda bulunan uç noktaları zaman uyumsuz olarak bildirilir avantajdır. Nasıl çalıştığını görmek için Client.cs dosyasını açın. Not <xref:System.ServiceModel.Discovery.DiscoveryClient> nesnesi iki Temsilciler, olay işleyicilerinin sahiptir. Bir temsilci çağrılır bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> olayı oluşturulur ve başka her zaman çağrılır bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayı oluşturulur. Örnek, uygulamanızda bu düzeni nasıl kullanabileceği gösterir.  
  
> [!NOTE]
>  Bu örnek HTTP uç noktaları kullanır ve çalıştırmak için uygun URL'yi ACL'leri eklenmesi gerekir. Daha fazla bilgi için [yapılandırma HTTP ve HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir. Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler için kullanıcı adı ve etki alanı yerine isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AsyncFind.sln açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug veya \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug dizine gidin ve Service.exe çalıştırın.  
  
4.  Hizmet başlatıldıktan sonra \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug veya WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug dizine gidin ve Client.exe çalıştırın.  
  
5.  İstemci bulun ve hizmet çağrısı gözlemleyin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Ayrıca Bkz.
