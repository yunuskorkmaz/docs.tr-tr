---
title: "İşlenen sıraları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11d1d0d3481fb575abd01894db631e24c50b6d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-queues"></a>İşlenen sıraları
Bu örnek, kuyruklar ve işlemlerde tümleştirmek gösterilmiştir [!INCLUDE[wf](../../../../includes/wf-md.md)] güvenilir ve ölçeklenebilir hizmetler oluşturmak için. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` istemci iş akışında kullanarak bir işlem altında kuyruğa ileti göndermek için kullanılan <xref:System.ServiceModel.NetMsmqBinding>. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> sunucuda kuyruktan ileti alma ve iş akışı aynı işlem altında durumunu güncelleştirmek için kullanılır.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>ve içerik tabanlı bağıntı.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte, kapsamdaki özellikleri göstermek için bir `RewardsPoints` iş akışı hizmeti oluşturulduğunda, hangi kazanılan ve belirli bir hesap için kullanılan noktalarını izler. İstemcinin kullandığı <xref:System.Activities.WorkflowInvoker> sıra çeşitli istekleri gönderme benzetimini yapmak için. Bir işlem altında kuyruğa ileti gönderme <xref:System.ServiceModel.Activities.Send> etkinlik içine yerleştirilebilir <xref:System.Activities.Statements.TransactionScope.Body%2A> , bir <xref:System.Activities.Statements.TransactionScope>. Bu örnekte, istemciyi nasıl sıraya alınan iletileri göstermek için sunucu tarafından izlenen ilk çalıştıran istemci ve sunucu uygulamaları ayırırsınız.  
  
 İstemci işlemi tamamlandıktan sonra hizmeti barındırılan ve yapılandırılır. Bunu açar açmaz zaten sırasına yerleştirilecek iletileri işleme başlatır. Her ileti aldı ve aynı sunucu işlemi altında işlenebilir. Bu örnekte, alınan ilk iletisidir bir `CreateAccount` örneği oluşturur ve hesap adını temel alarak içerik bağıntı başlatır isteği istek iletisinin bir parçası olarak geçirildi. Gerçek Hayatta, aşağıdaki iki beklediğiniz hizmet türünü modellemek için <xref:System.ServiceModel.Activities.TransactedReceiveScope> işlem etkinlikleri `AddPoints` ve `UsePoints` iletileri içinde paralel dalları yerleştirilir bir `while` böylece bunlar işleme döngüsü herhangi bir sırada sürekli iletileri.  
  
 <xref:System.Activities.Statements.TransactionScope>ve <xref:System.ServiceModel.Activities.TransactedReceiveScope> her bir örtük Kalıcılık noktasına sahip kendi kapsamları sonunda, böylece bu etkinlikler kullanarak [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kuyruklarla birleştirilmiş akışınız, iletileri olduğunu sağlarken yanında, tutarlı bir durumdan diğerine taşımak için bir güvenilir yoludur hiçbir zaman kesildi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme ve MSMQ Yapılandırma. Bkz: [Message Queuing'i yükleme](http://go.microsoft.com/fwlink/?LinkId=178526) Ayrıntılar için.  
  
2.  Bir komut satırında aşağıdaki komutu çalıştırarak MSDTC çalıştığından emin olun. `net start msdtc`  
  
3.  Projeyi derlemek ve yürütülebilir dosya veya projede açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve hata ayıklama menüsünden başlangıç seçeneği seçin. İlk olarak, sıra oluşturulur, sonra istemci çalışır ve kuyruğa ileti gönderir ve son olarak hizmeti başlatılır ve iletileri işlenir. Programdan çıkmak için ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
