---
title: İçeriğe dayalı bağıntı
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: b90d076d96e1bae5c44dc1c2b06f826d256f7463
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518838"
---
# <a name="content-based-correlation"></a>İçeriğe dayalı bağıntı
Bu örnek gösterilmektedir nasıl Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>) içerik tabanlı birden çok içerik tabanlı correlations.and bağıntı ile kullanılabilir. Bu senaryoda, satın alma siparişi kimliği temel alarak bir bağıntı önce başlatılır ve başka bir bağıntı daha sonra müşteri kimliği temel alınarak oluşturulur Bu durum gösterilir ve nasıl bir <xref:System.ServiceModel.Activities.Receive> etkinlik hem mevcut bir bağıntı izleyin ve aynı gelen iletisini temel alarak yeni bir bağıntı başlatma.  
  
## <a name="demonstrates"></a>Gösteriler  
 Mesajlaşma etkinlikleri ve içerik tabanlı bağıntı  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, birden çok içerik tabanlı bağıntıları kullanmayı gösterir.  Bu senaryoda, satın alma siparişi kimliği temel alarak bir bağıntı önce başlatılır ve başka bir bağıntı daha sonra müşteri kimliği temel alınarak oluşturulur  Kullanarak bağıntıları basamaklı bir <xref:System.ServiceModel.Activities.Receive> var olan bir bağıntı (PurchaseOrderID) izleyen hem de yeni bir bağıntı (CustomerID) başlatır etkinlik tabanlı aynı gelen ileti üzerinde.  Bunu başarmak için <xref:System.ServiceModel.Activities.Receive> aktivitesi kullanır <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> ve <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özellikleri.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.  
  
2.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CascadingCorrelation.sln çözüm dosyasını açın.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
4.  Sunucu çalıştırmak için F5 tuşuna basın.  
  
5.  Hizmet, Çözüm Gezgini'nde, iletileri için hazır ve dinleme sonra istemci projesine sağ tıklayın ve çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`