---
title: "TransactedReceiveScope kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9d20e6280b440e3b1595dd25535857ac7828d2d0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="use-of-transactedreceivescope"></a>TransactedReceiveScope kullanımı
Bu örnek kullanarak bir sunucu için bir istemciden bir işlem akışı gösterilmektedir <xref:System.Activities.Statements.TransactionScope> istemci üzerinde yeni bir işlem oluşturmak için ve bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> akışlı bir işlem içeren bir ileti almak ve sunucu üzerindeki işlem ömrü kapsam için. Örnek, istemci ve sunucu rolleri dolduran iki projeden oluşan.  
  
## <a name="client-application"></a>İstemci uygulaması  
 İstemci uygulaması dağıtılmış işlem kimliği yazdırır, sunucuya bir ileti gönderir, işlem akışlar, yanıtı alır, dağıtılmış işlem kimliği yeniden yazdırır ve tamamlandıktan bir iş akışı çalıştırır. Dağıtılmış işlem kimliği başlangıçta baskı siparişi olduğunda, işlem hala yalnızca yerel olarak boş bir GUID olur.  
  
## <a name="server-application"></a>Sunucu uygulaması  
 Sunucu projesi benzer, ancak, iş akışı içinde barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> istemciden gelen iletiyi için bunu bir uç noktası üzerinde dinleme gerekir çünkü. İş akışı üzerinde ortalanır <xref:System.ServiceModel.Activities.TransactedReceiveScope>, istemciden akışlı işlem aldığı gönderildi, dağıtılmış işlem kimliği yazdırır ve yanıt istemciye gönderir. ileti yazdırır. Dağıtılmış işlem kimliği boş olmayan GUID ve işlem algılayan bir etkinlik gövdesi ile eklendiyse sunulmuştur <xref:System.ServiceModel.Activities.TransactedReceiveScope>, akan işlem altında yürütülür.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  TransactedReceiveScope.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Derleme başarılı olduktan sonra çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla**. İletişim kutusundan seçin **birden fazla başlangıç projesi** ve her iki projeleri için eylem olun **Başlat**.  
  
4.  F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
    > [!NOTE]
    >  Sunucu, istemci başlatmadan önce çalışmalıdır. Barındırma hizmeti konsol penceresinden çıktı ne zaman başlatıldığını belirtir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`