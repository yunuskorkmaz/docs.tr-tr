---
title: İşlemi yapılmış kuyruklar
ms.date: 03/30/2017
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
ms.openlocfilehash: db6a9686334eefb02b9360827a23ca8363127eb5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535510"
---
# <a name="transacted-queues"></a>İşlemi yapılmış kuyruklar
Bu örnek, kuyrukları ve işlem içinde Windows Workflow Foundation (güvenilir ve ölçeklenebilir hizmetler oluşturmak için WF) tümleştirme gösterilmektedir. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` kullanarak bir işlem altında bir kuyruğa ileti göndermek için kullanılan istemci iş akışında <xref:System.ServiceModel.NetMsmqBinding>. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> sunucuda kuyruktan ileti alma ve aynı işlem altında bir iş akışı durumunu güncelleştirmek için kullanılır.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>ve içerik temelli bağıntı.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte, ele alınan özelliklerin göstermek için bir `RewardsPoints` iş akışı hizmeti oluşturulur, hangi kazanılan ve belirli bir hesap için kullanılan noktalarını izler. İstemcinin kullandığı <xref:System.Activities.WorkflowInvoker> çeşitli istekler kuyruğa ileti gönderme benzetimini yapmak için. Bir işlem altında kuyruğuna bir ileti göndermek için <xref:System.ServiceModel.Activities.Send> etkinlik içine yerleştirilebilir <xref:System.Activities.Statements.TransactionScope.Body%2A> , bir <xref:System.Activities.Statements.TransactionScope>. Bu örnekte, istemci sunucu nasıl kuyruğa alınmış iletiler göstermek için ilk olarak, çalışan istemci ve sunucu uygulamaları ayırmak.  
  
 İstemci işlemi tamamlandıktan sonra hizmet barındırılan ve yapılandırılır. Bunu açar açmaz kuyrukta yerleştirmiş olduğunuz iletilerini işleme başlar. Her bir ileti alındı ve altında aynı sunucu işlemi işlenen. Bu örnekte alınan ilk ileti olduğunu bir `CreateAccount` örneği oluşturur ve başlatır hesap adına göre içerik bağıntı isteği, istek iletisinin bir parçası olarak geçirildi. Aşağıdaki iki gerçek dünyada beklediğiniz hizmet türü model <xref:System.ServiceModel.Activities.TransactedReceiveScope> işlem etkinlikleri `AddPoints` ve `UsePoints` iletileri içinde paralel dallarından yerleştirildiğinde bir `while` bunları işleyebilmesi döngü herhangi bir sırada sürekli olarak iletiler.  
  
 <xref:System.Activities.Statements.TransactionScope> ve <xref:System.ServiceModel.Activities.TransactedReceiveScope> her bir Kalıcılık örtülü noktasına sahip kendi kapsamları sonunda, bu etkinlikleri kullanarak [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kuyrukları ile birlikte, iş akışınızı, iletilerin alınmasını sağlarken yanında, tutarlı bir durumdan diğerine taşımak için bir güvenilir yoludur hiçbir zaman kaybolur.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme ve MSMQ Yapılandırma. Bkz: [yükleme Message Queuing](https://go.microsoft.com/fwlink/?LinkId=178526) Ayrıntılar için.  
  
2.  Bir komut satırında aşağıdaki komutu yürüterek MSDTC çalıştığından emin olun. `net start msdtc`  
  
3.  Projeyi Derle ve yürütülebilir dosyayı veya projeyi açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve hata ayıklama menüsünden bir başlatma seçeneğini belirleyin. İlk olarak, sıra oluşturulur, sonra istemci çalışır ve kuyruğuna ileti gönderir ve son olarak hizmeti başlatır ve iletileri işlenir. Programdan çıkmak için ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
