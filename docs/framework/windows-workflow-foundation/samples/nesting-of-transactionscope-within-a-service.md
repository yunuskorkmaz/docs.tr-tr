---
title: TransactionScope'u bir hizmet içinde iç içe geçirme
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: cf73c0c2d061f1c997a8ade5d7b2bf61887915ca
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700030"
---
# <a name="nesting-of-transactionscope-within-a-service"></a>TransactionScope'u bir hizmet içinde iç içe geçirme
Bu örnek iki senaryo oluşur, çalışan nasıl ele alınacağını gösteren <xref:System.Activities.Statements.TransactionScope> hizmetinden etkinlik örnekleri. İşlem kullanarak ilk kez başlatılan <xref:System.Activities.Statements.TransactionScope> istemcide yeni bir işlem oluşturmak için etkinlik ve <xref:System.ServiceModel.Activities.TransactedReceiveScope> almak için sunucu üzerinde işlem ömrü kapsam. İlk senaryoda hizmetinde ikincil çalıştıran <xref:System.Activities.Statements.TransactionScope> iç içe göstermek için etkinlik <xref:System.Activities.Statements.TransactionScope> hizmetindeki etkinlikler. İkinci senaryoda zaman aşımları nasıl uymaya gösterilmektedir içinde iç içe <xref:System.Activities.Statements.TransactionScope> etkinlikler.  
  
## <a name="client-application"></a>İstemci uygulaması  
 İstemci uygulaması başlatan bir iş akışını çalıştıran bir <xref:System.Activities.Statements.TransactionScope> etkinlik, dağıtılmış işlem kimliği yazdırır sunucusuna bir ileti gönderir, işlem akışları, yanıtı alır, dağıtılmış işlem kimliği yeniden yazdırır ve tamamlar. Her hizmet senaryo için bunu bir kez yapar.  
  
## <a name="server-application"></a>Sunucu uygulaması  
 Sunucu projesi barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost>, istemciden gelen iletiyi dinlemek için uç nokta oluşturur. İş akışı üzerinde ortalanmış <xref:System.ServiceModel.Activities.TransactedReceiveScope>, dağıtılmış işlem kimliği yazdırır ve ardından ikinci bir yürütür, istemciden akışlı işlem aldığı <xref:System.Activities.Statements.TransactionScope> etkinlik. Bu senaryoda, işlem başarıyla tamamlandı. İkinci senaryoda, gövdesi <xref:System.Activities.Statements.TransactionScope> etkinlik 5 saniyelik gecikme ve işlem için zaman aşımı süresi iki saniye olarak ayarlanır. İşlem hareketi zaman zaman iptal edildi.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  TransactionServiceExample.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.  
  
3.  Derleme başarılı olana sonra çözümü sağ tıklatın ve seçin **başlangıç projelerini Ayarla**. İletişim kutusundan **birden fazla başlangıç projesi** ve iki proje için bir eylem olduğundan emin olun **Başlat**.  
  
4.  F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak, CTRL + F5 tuşlarına basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** hata ayıklama olmadan çalıştırmak için menü.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
