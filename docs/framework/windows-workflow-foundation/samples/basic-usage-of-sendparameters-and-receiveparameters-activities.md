---
title: "SendParameters ve ReceiveParameters etkinliklerin temel kullanım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c3b6f189f1a2564662af89961c9363f025ae8c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>SendParameters ve ReceiveParameters etkinliklerin temel kullanım
Bu örnek kullanımı gösterilmiştir <xref:System.ServiceModel.Activities.SendParametersContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlikler. Hizmet, dize bağımsız değişkeni alır ve istemciye geri giriş görüntülemektedir bir işlemi sunar. Örnek ileti bu etkinlikler parametrelerini ayarlamak nasıl gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Bu örnek kullanma  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.  
  
2.  İlk [çözüm temel dizin] \EchoWorkflowService\bin\debug oluşturulan EchoWorkflowService uygulamayı çalıştırın.  
  
3.  İkinci olarak, [çözüm temel dizin] \EchoWorkflowClient\bin\debug oluşturulan EchoWorkflowClient uygulamayı çalıştırın.  
  
4.  İstemci Yankı işlemi hizmet üzerinde çağıran ve sonuçları yazdırır. Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
