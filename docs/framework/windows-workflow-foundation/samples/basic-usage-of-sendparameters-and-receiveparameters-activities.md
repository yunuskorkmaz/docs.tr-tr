---
title: SendParameters ve ReceiveParameters etkinliklerinin temel kullanımı
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504014"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>SendParameters ve ReceiveParameters etkinliklerinin temel kullanımı
Bu örnek, kullanımını gösterir. <xref:System.ServiceModel.Activities.SendParametersContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlikler. Hizmet, bir dize bağımsız değişkeni alır ve giriş istemcisine yankılayan tek bir işlem sunar. Örnek, bu ileti etkinlikleri parametrelerini ayarlama işlemi gösterilmektedir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Bu örnek kullanma  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi derleyin.  
  
2.  İlk [çözüm temel dizini] \EchoWorkflowService\bin\debug içinde oluşturulan EchoWorkflowService uygulamayı çalıştırın.  
  
3.  İkinci olarak, [çözüm temel dizini] \EchoWorkflowClient\bin\debug içinde oluşturulan EchoWorkflowClient uygulamayı çalıştırın.  
  
4.  İstemci, Echo hizmet işlemi çağırır ve sonuçları yazdırır. Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.