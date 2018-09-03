---
title: Flowchart ve Pick birleşimini kullanarak senaryosu
ms.date: 03/30/2017
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
ms.openlocfilehash: b0f8e884a8a6c62c4e7edaf5cc9727bf7bfe8603
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483930"
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Flowchart ve Pick birleşimini kullanarak senaryosu
Bu örnek bir birleşimini kullanarak bir kronometre basit senaryonun nasıl uygulanacağını gösterir <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler. Alma ve gönderme Pick etkinliği içinde kronometre olaylarını dinleyecek şekilde kullanır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse (indirme sayfası) Git tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Aşağıdaki tabloda, bu örnekte projeleri listeler.  
  
|Proje adı|Açıklama|  
|-|-|  
|StopWatchService|Bu proje bir durum makinesindeki bir birleşimi kullanılarak kronometre örnek uygulamasını içerir <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler.<br /><br /> <xref:System.Activities.Statements.Pick> Etkinliğinde 3 <xref:System.Activities.Statements.PickBranch> deyimleri içinde <xref:System.Activities.Statements.Pick.Branches%2A> dinler özelliği `GetStart`, `GetStop` ve `GetOff` olayları. Gelen olay tabanlı, dalları biri için Tetikleyiciler etkinleştirmek ve karşılık gelen <xref:System.Activities.Statements.PickBranch.Action%2A> tetiklenir. İçinde <xref:System.Activities.Statements.PickBranch.Action%2A> özelliği var. bir <xref:System.Activities.Statements.Switch%601> geçiş yasal geçiş olup olmadığını ve eğer ise, değerlendirilen ifade `currentState` özelliği için geçiş durumu güncelleştirildi ve istemciye gönderilen.<br /><br /> <xref:System.Activities.Statements.FlowDecision> Etkinlik sonunda <xref:System.Activities.Statements.Flowchart> değerlendirir `currentState` durumu terminal olup olmadığını belirlemek için özellik. İse, iş akışı sona erer; Aksi takdirde, döngüler tekrar başlangıcını denetim <xref:System.Activities.Statements.Pick> burada iş akışını bekler daha fazla kronometre etkinlik için etkinlik.|  
|StopWatchClient|Bu basit çeşitli kronometre olaylarla etkinlik birleşimleri gönderip gönderen bir basit sıralı iş akışı konsol uygulamasıdır.|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]açın StateMachineWithPick.sln çözüm dosyası.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Gelen StopWatchService.exe Başlat [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] .exe dosyasına sağ tıklayarak ve seçerek bir yönetici olarak **yönetici olarak çalıştır**.  
  
    1.  StateMachineWithPick\CS\StopWatchService\bin\Debug klasöre gidin.  
  
    2.  StopWatchService.exe dosyaya sağ tıklayıp **yönetici olarak çalıştır**.  
  
4.  StopWatchClient istemci uygulamasının içinden başlatın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  İçinde **Çözüm Gezgini**seçin **StopWatchClient** sağ tıklayın ve proje **başlangıç projesi olarak ayarla**.  
  
    2.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
5.  Durumu geçişleri görüntülemek StopWatchService.exe için konsol penceresine dönün.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`