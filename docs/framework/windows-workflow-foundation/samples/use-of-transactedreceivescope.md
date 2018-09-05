---
title: TransactedReceiveScope kullanımı
ms.date: 03/30/2017
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
ms.openlocfilehash: bc1c418f3fa116f5e1c1647af3543a38122842f5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501648"
---
# <a name="use-of-transactedreceivescope"></a>TransactedReceiveScope kullanımı
Bu örnek, kullanarak bir sunucu için bir istemciden bir işlem akışı gösterilmektedir <xref:System.Activities.Statements.TransactionScope> istemcide yeni bir işlem oluşturmak için ve bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> akışlı bir işlem içeren bir ileti alma ve sunucu üzerinde işlem ömrü kapsam. Örnek, istemci ve sunucu rollerini dolduran iki projeden oluşan.  
  
## <a name="client-application"></a>İstemci uygulaması  
 İstemci uygulamasının dağıtılmış işlem kimliği yazdırır, sunucusuna bir ileti gönderir, işlem akışları, yanıtı alır, dağıtılmış işlem kimliği yeniden yazdırır ve tamamlanan bir iş akışı çalıştırır. Dağıtılmış işlem kimliği başlangıçta yazdırır olduğunda, işlem yine de yalnızca yerel olduğundan bir boş GUID değeridir.  
  
## <a name="server-application"></a>Sunucu uygulaması  
 Sunucu projesi benzer; ancak, iş akışı içinde barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> olduğundan, bir uç noktaya istemciden gelen iletiyi dinlemeye devam etmesi gerekir. İş akışı üzerinde ortalanmış <xref:System.ServiceModel.Activities.TransactedReceiveScope>, istemciden akışlı işlem aldığı gönderildi, dağıtılmış işlem kimliği yazdırır ve yanıt istemciye gönderir ileti yazdırır. Dağıtılmış işlem kimliği boş olmayan GUID ve hareket algılayan bir etkinlik gövdesi ile eklendiyse sunulmuştur <xref:System.ServiceModel.Activities.TransactedReceiveScope>, akışlı işlem altında yürütülür.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  TransactedReceiveScope.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.  
  
3.  Derleme başarılı olana sonra çözümü sağ tıklatın ve seçin **başlangıç projelerini Ayarla**. İletişim kutusundan seçin **birden fazla başlangıç projesi** ve iki proje için bir eylem olduğundan emin olun **Başlat**.  
  
4.  F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak, CTRL + F5 tuşlarına basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** hata ayıklama olmadan çalıştırmak için menü.  
  
    > [!NOTE]
    >  Sunucu, istemci başlatılmadan önce çalıştırılması gerekir. Barındırma hizmeti bir konsol penceresi çıktısı, ne zaman başladığını belirtir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`