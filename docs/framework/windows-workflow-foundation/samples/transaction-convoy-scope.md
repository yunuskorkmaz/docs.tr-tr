---
title: İşlem Convoy kapsamı
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: 4b053c15768a20ade4a469c9a40af797f49c268b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-convoy-scope"></a>İşlem Convoy kapsamı
Bu örnek nasıl paralel etkinlik düzeni ile birlikte Mesajlaşma Convoy oluşturulduğunu gösteren bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> burada birkaç işlem oluşabilir tüm aynı işlem altında herhangi bir sırada bir protokol modellemek için. Bu örnek ayrıca gösterir nasıl bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> istemci kullanmayan şekilde bir sunucuya akıtılan değil, yeni bir işlem otomatik olarak oluşturur işlemler kullanın.  
  
 Örnek istemci ve sunucu temsil eden iki iş akışı projeleri oluşur. İstemci projesi bir bağıntı başlatır ve mesajlaşma etkinlikleri geri kalanı için bir işlem kapsamı başlatır sunucu iş akışı bootstrap isteyen bir ileti göndererek başlayan bir iş akışı çalıştırır. İstemci <xref:System.Activities.Statements.Sequence> etkinlik içeren bir ilk <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> çifti ve ardından bir <xref:System.Activities.Statements.Parallel> üç dalları etkinlikle. Her dal sunucuya tek yönlü bir ileti gönderir. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Özelliği <xref:System.Activities.Statements.Parallel> etkinlik ayarlanmış `false` böylece tüm üç dalları tamamlayın.  
  
 Sunucu iş akışı Mesajlaşma etkinlikleri iletişimi sunucu tarafı doğru yerleştirilir ve içinde yer alan dışındaki istemci iş akışına benzer bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik tüm Bitti'yi çalışmak üzere aynı işlemde yürütür. Sunucuda ilk ileti alındığında, bir işlem oluşturulur ve kapsamını ortam yapılan <xref:System.ServiceModel.Activities.TransactedReceiveScope> bu kapsam içinde herhangi bir etkinlik işlem erişebilmesi için gövde. Bundan sonra tüm alan paralel olarak yürütün. Tüm alır gereken tam olarak bir kez üzerinde paralel etkinlik tamamlanma koşul tarafından açıklandığı gibi yürütün. Sonunda örtük Kalıcılık noktanız var <xref:System.ServiceModel.Activities.TransactedReceiveScope> gövde ve sürdürme işlemi aynı işlemde yürütülen de.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ParallelConvoySample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Her iki proje başlatmak için ayarlandığından emin olun.  
  
    1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla**.  
  
    2.  Seçin **birden fazla başlangıç projesi** ve her iki projeleri için eylem ayarlandığından emin olun **Başlat**.  
  
4.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
     Sunucu baskı siparişi `Server is running`, sunucunun belirten hazırdır.  
  
     Örnek başlatmak için istemci konsol penceresinde herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`