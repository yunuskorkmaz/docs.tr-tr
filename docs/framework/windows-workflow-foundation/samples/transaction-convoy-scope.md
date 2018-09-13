---
title: İşlem Konvoy kapsamı
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: fa1da6df5ad5256665610c9b3c2df7d706cef63c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705290"
---
# <a name="transaction-convoy-scope"></a>İşlem Konvoy kapsamı
Bu örnek, paralel bir etkinlik deseni ile birlikte Mesajlaşma Konvoy oluşturma işlemini gösterir. bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> burada işlemlerinin sayısı gerçekleşebilir tümü aynı işlem altında herhangi bir sırada bir protokol model. Bu örnek ayrıca gösterir nasıl bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> istemci olmayan haline bir sunucuya akıtılan değil, otomatik olarak yeni bir işlem oluşturur işlemler kullanın.  
  
 Örnek istemci ve sunucu temsil eden iki iş akışı projeleri oluşur. İstemci projesi, bir bağıntıyı başlatır ve mesajlaşma etkinlikleri geri kalanı için bir işlem kapsamı başlatılır sunucu iş akışı önyükleme için bir ileti göndererek başlayan bir iş akışı çalıştırır. İstemci <xref:System.Activities.Statements.Sequence> etkinliği içeren bir ilk <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> çifti ve ardından bir <xref:System.Activities.Statements.Parallel> üç dallarıyla etkinlik. Her dal sunucuda tek yönlü bir ileti gönderir. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Özelliği <xref:System.Activities.Statements.Parallel> etkinlik ayarlandığında `false` üç tüm dallar tamamlandıktan böylece.  
  
 Sunucu iş akışı Mesajlaşma etkinlikleri iletişimi sunucu tarafı doğru yerleştirilir ve içinde yer alan dışındaki istemci iş akışına benzer bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği tüm çalışma böylece aynı işlemde yürütür. İlk iletinin sunucuda alındığında, bir işlem oluşturulur ve kapsamını ortam yapılan <xref:System.ServiceModel.Activities.TransactedReceiveScope> bu kapsam içinde herhangi bir etkinliği işlem erişebilmesi için gövde. Bundan sonra tüm alan paralel olarak çalıştırmak. Gereken tüm alan tam bir kez tamamlama koşul üzerinde paralel etkinlik açıklandığı yürütün. Sonunda bir örtük Kalıcılık noktası var. <xref:System.ServiceModel.Activities.TransactedReceiveScope> gövdesi ve sürdürme işlemi aynı işlem altında yürütülen de.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ParallelConvoySample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Her iki proje başlatılacak şekilde ayarlandığından emin olun.  
  
    1.  İçinde **Çözüm Gezgini**, çözümü sağ tıklatın ve seçin **başlangıç projelerini Ayarla**.  
  
    2.  Seçin **birden fazla başlangıç projesi** ve her iki projeleri için eylem ayarlandığından emin olun **Başlat**.  
  
4.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
     Sunucu yazdırır `Server is running`, sunucunun gösteren hazırdır.  
  
     Örneği başlatmak için istemci konsol penceresinde herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`