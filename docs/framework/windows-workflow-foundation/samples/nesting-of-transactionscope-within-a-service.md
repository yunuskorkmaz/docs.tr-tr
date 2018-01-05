---
title: "TransactionScope iç içe bir hizmet kapsamındaki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c4e51f65df010f466f43c2018d9b1eec6e4ca58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="nesting-of-transactionscope-within-a-service"></a>TransactionScope iç içe bir hizmet kapsamındaki
Bu örnek iki senaryoları oluşur çalıştırılan nasıl yapılacağını gösteren <xref:System.Activities.Statements.TransactionScope> bir hizmet kapsamındaki etkinlik örnekleri. İşlem kullanarak ilk kez başlatılan <xref:System.Activities.Statements.TransactionScope> istemci üzerinde yeni bir işlem oluşturmak için etkinlik ve <xref:System.ServiceModel.Activities.TransactedReceiveScope> almak ve sunucu üzerindeki işlem ömrü kapsam için. İkincil bir hizmet içinde ilk senaryoda çalıştıran <xref:System.Activities.Statements.TransactionScope> iç içe göstermek için etkinlik <xref:System.Activities.Statements.TransactionScope> hizmet içinde etkinlikler. Ne zaman aşımlarını dikkate ikinci senaryo gösterilmektedir içinde iç içe <xref:System.Activities.Statements.TransactionScope> etkinlikler.  
  
## <a name="client-application"></a>İstemci uygulaması  
 İstemci uygulaması başlatır bir iş akışı çalıştıran bir <xref:System.Activities.Statements.TransactionScope> etkinlik, dağıtılmış işlem kimliği yazdırır sunucusuna bir ileti gönderir, işlem akışlar, yanıtını alır, dağıtılmış işlem kimliği yeniden yazdırır ve tamamlar. Bunu bu kez, her hizmet senaryo için yapar.  
  
## <a name="server-application"></a>Sunucu uygulaması  
 Sunucu projesi içinde barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost>, istemciden gelen iletiyi dinlemek için bitiş noktası oluşturur. İş akışı üzerinde ortalanır <xref:System.ServiceModel.Activities.TransactedReceiveScope>, dağıtılmış işlem kimliği yazdırır ve ikinci bir yürütür, istemciden akışlı işlem aldığı <xref:System.Activities.Statements.TransactionScope> etkinlik. İlk senaryoda işlem başarıyla tamamlandı. İkinci senaryoda, gövdesini <xref:System.Activities.Statements.TransactionScope> etkinlik beş saniyelik gecikme ve işlem için zaman aşımı süresi iki saniye olarak ayarlanır. İşlem hareketi zaman zaman iptal edilir.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  TransactionServiceExample.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Derleme başarılı olduktan sonra çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla**. İletişim kutusundan **birden fazla başlangıç projesi** ve her iki projeleri için eylem olun **Başlat**.  
  
4.  F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
