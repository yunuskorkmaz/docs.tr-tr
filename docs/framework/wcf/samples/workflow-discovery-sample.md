---
title: "İş Akışı Keşif Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba400a4476ffd2589af1d5e7d3e0ca5661102f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-discovery-sample"></a>İş Akışı Keşif Örneği
Bu örnek bir iş akışı hizmeti bulunabilirlik yapma ve belirli bir hizmet için arar özel kod etkinlik yazmak nasıl gösterilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Bulma Bul etkinliği ve iş akışı kullanımı  
  
## <a name="discussion"></a>Tartışma  
 Örnek ilk bölümünde, bir iş akışı hizmeti bulunabilirlik yapılan Yapılandırması'nı kullanarak. Yapılandırma, özel meta verileri (örneğin, kapsam) hizmetiyle uygun şekilde uygulamak için de kullanılabilir. İstemci üzerinde örnek bulma aramak için belirli bir sözleşme eşleşen bir hizmetini kullanan bir özel kod aktivitesi kullanır. Daha sonra Gönder etkinliği tarafından kullanılan bir URI kodunu aktivite çıkarır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Bu örneği çalıştırmak için doğru URL ACL olmalıdır HTTP uç noktaları kullanır (bkz [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için). Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütülürken uygun ACL'ler eklemeniz gerekir. Kabuğunuzu değişken biçimi anlamıyorsa etki alanı ve kullanıcı adı şu bağımsız değişkenleri değiştirin.  
  
     **Netsh http add urlacl url = http: / / +: 8000 / kullanıcı etki alanı % =\\% UserName %**  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
