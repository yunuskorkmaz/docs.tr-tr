---
title: Desen otomatik olarak Onayla
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3595e501341f64883ce2552f0a3c0850691f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="auto-confirm-pattern"></a>Desen otomatik olarak Onayla
Bu örnek özel bir gösteren çalıştıran üç senaryoları oluşur `AutoConfirmScope` etkinlik. İlk örnek burada ikinci ve üçüncü iç içe geçmiş içinde dört compensable etkinlikler dizisini aktarılmadığı gösterilir bir `AutoConfirmScope`. İkinci örnek aynı dördüncü yürütme sonrasında oluşan bir özel durum ile gösterilir <xref:System.Activities.Statements.CompensableActivity>. Üçüncü senaryo aynı içinde gerçekleşen bir özel durum ile gösterilir `AutoConfirmScope` saniye sonra <xref:System.Activities.Statements.CompensableActivity> tamamlar.  
  
 Örnek, tüm alt compensable etkinlikleri kapsamı başarıyla tamamlanmasından sonra burada onaylanır auto-confirm düzeni gösterir. Bunlar artık dengelendi onaylanıp veya gibi bu deseni tüm alt compensable etkinlikleri, ömrü tanımlar.  
  
 Kapsam oluşan bir <xref:System.Activities.Statements.TryCatch> nerede <xref:System.Activities.Statements.TryCatch.Try%2A> bir iç <xref:System.Activities.Statements.CompensableActivity>. Kullanıcı tarafından belirtilen gövdesi `AutoConfirmScope` iç gövdesi <xref:System.Activities.Statements.CompensableActivity>. Bu dahili zaman <xref:System.Activities.Statements.CompensableActivity> tamamlar, onu üreten bir <xref:System.Activities.Statements.CompensationToken> çıkış-bağımsız değişken olarak. `AutoConfirmScope` Kullanan bir <xref:System.Activities.Statements.TryCatch.Finally%2A> belirteci bir olup üretilen ve iç onaylar sonra olup olmadığını denetlemek için <xref:System.Activities.Statements.CompensableActivity>. İç <xref:System.Activities.Statements.CompensableActivity> kendi gövdesinde bulunabilir compensable etkinlikler için varsayılan maaş çağırır.  
  
 İlk senaryoda, iş akışının aktarılmadığı gösterilir ve ikinci ve üçüncü compensable etkinlikler iş akışı tamamlandığında ve birinci ve dördüncü onaylanıp başlatıldığında zaten onaylanır gösterir. Bu üç, iki, dört ve bir onay sırasını oluşturur.  
  
 İkinci senaryo dört compensable etkinlikleri tamamlandıktan sonra bir özel durum gösterir. İkinci ve üçüncü compensable etkinlikleri zaten oldukları onaylandığı çünkü etkilenmemiştir ancak biri ve dört dengelendi. Bu üretir üç onaylayın, iki onaylayın, dört dengelemek ve şunlardan dengelemek.  
  
 Başarısız yürütülmesi son senaryo gösterilmektedir `AutoConfirmScope`. Bu senaryoda, ikinci tamamlandıktan sonra bir özel durum oluşur <xref:System.Activities.Statements.CompensableActivity>. Üçüncü ve dördüncü compensable etkinlikleri yürütülmedi olduğundan, bunlar etkilenmez. Kapsam başarıyla tamamlanmadığı ikinci <xref:System.Activities.Statements.CompensableActivity> doğrulanmamış. Bu oluşturur ve iki sonra biri maaş sırası.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], AutoConfirmSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`