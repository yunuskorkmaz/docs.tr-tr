---
title: "Durum makinesi Akış Çizelgesi ve çekme birleşimini kullanarak senaryosu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39ae1be025e3b888fff8b46ebbc45832c218dda7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Durum makinesi Akış Çizelgesi ve çekme birleşimini kullanarak senaryosu
Bu örnek, bir birleşimini kullanarak basit kronometre senaryoları uygulayacak gösterilmiştir <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler. Alma ve gönderme içinde çekme etkinlik kronometre olaylarını dinleyecek şekilde kullanır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse (indirme) gidin tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Aşağıdaki tabloda, bu örnek projelerinde listeler.  
  
|Proje adı|Açıklama|  
|-|-|  
|StopWatchService|Bu proje bir birleşimini kullanarak kronometre örneği için durum makinesinin uyarlamasını içeren <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler.<br /><br /> <xref:System.Activities.Statements.Pick> Etkinlik sahip 3 <xref:System.Activities.Statements.PickBranch> deyimleri içinde <xref:System.Activities.Statements.Pick.Branches%2A> dinlemek özelliği `GetStart`, `GetStop` ve `GetOff` olaylar. Dalları biri için Tetikleyiciler gelen olaya bağlı olarak, etkinleştirme ve karşılık gelen <xref:System.Activities.Statements.PickBranch.Action%2A> tetiklenir. İçinde <xref:System.Activities.Statements.PickBranch.Action%2A> özelliği var. bir <xref:System.Activities.Statements.Switch%601> geçişi yasal geçiş olup olmadığını ve bu doğruysa değerlendirir deyimi `currentState` özelliği geçirme durumuna güncelleştirildi ve istemciye gönderilen.<br /><br /> <xref:System.Activities.Statements.FlowDecision> Sonunda etkinlik <xref:System.Activities.Statements.Flowchart> değerlendirir `currentState` durumu terminal olup olmadığını belirlemek için özellik. Bu durumda, iş akışı sona erer; Aksi takdirde, döngüler başlangıcını dön kontrol <xref:System.Activities.Statements.Pick> etkinliği iş akışı için daha fazla kronometre olayları burada bekler.|  
|StopWatchClient|Bu basit çeşitli kronometre olaylarla etkinlik birleşimleri gönderip gönderen bir basit sıralı iş akışı konsol uygulamasıdır.|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], açık StateMachineWithPick.sln çözüm dosyası.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Gelen StopWatchService.exe Başlat [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] .exe dosyasına sağ tıklatarak ve seçerek yönetici olarak **yönetici olarak çalıştır**.  
  
    1.  StateMachineWithPick\CS\StopWatchService\bin\Debug klasöre gidin.  
  
    2.  StopWatchService.exe dosyasını sağ tıklatın ve seçin **yönetici olarak çalıştır**.  
  
4.  StopWatchClient istemci uygulaması içinden Başlat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  İçinde **Çözüm Gezgini**seçin **StopWatchClient** sağ tıklayın ve proje **başlangıç projesi olarak ayarla**.  
  
    2.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
5.  İçin durumu geçişleri görüntülemek StopWatchService.exe konsol penceresine dönün.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`