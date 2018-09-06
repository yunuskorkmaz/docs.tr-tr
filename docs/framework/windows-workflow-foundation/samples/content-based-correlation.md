---
title: İçerik temelli bağıntı
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: c0367f480701468dcd5024ea3439bdcd38acc78f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731728"
---
# <a name="content-based-correlation"></a>İçerik temelli bağıntı
Bu örnek gösterir nasıl Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>) birden çok içerik tabanlı correlations.and içerik temelli bağıntı ile kullanılabilir. Bu senaryoda, bir satın alma siparişi Kimliğine dayanarak bir bağıntı önce başlatılır ve ardından başka bir bağıntı daha sonra müşteri kimliğini temel alan oluşturulur Bu durum gösterilir ve nasıl bir <xref:System.ServiceModel.Activities.Receive> etkinlik hem mevcut bir bağıntı izleyin ve aynı gelen iletisini temel alarak yeni bir bağıntıyı başlatır.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma etkinlikleri ve içerik temelli bağıntı  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, birden çok içerik tabanlı bağıntılar kullanma işlemini gösterir.  Bu senaryoda, bir satın alma siparişi Kimliğine dayanarak bir bağıntı önce başlatılır ve ardından başka bir bağıntı daha sonra müşteri kimliğini temel alan oluşturulur  Bağıntıları kullanarak basamaklı bir <xref:System.ServiceModel.Activities.Receive> (CustomerID) yeni bir bağıntıyı başlatır ve var olan bir bağıntı (PurchaseOrderID) izleyen etkinlik tabanlı üzerinde aynı gelen ileti.  Bunu gerçekleştirmek için <xref:System.ServiceModel.Activities.Receive> etkinliği kullanan <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> ve <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özellikleri.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinlerle [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.  
  
2.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CascadingCorrelation.sln çözüm dosyasını açın.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
4.  Sunucu çalıştırmak için F5 tuşuna basın.  
  
5.  Hazır ve dinleme iletileri, Çözüm Gezgini'nde Hizmet başladıktan sonra istemci projesini sağ tıklayın ve çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`