---
title: Otomatik onaylama deseni
ms.date: 03/30/2017
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
ms.openlocfilehash: a032c05743b64fe58b0b187328b5216080ba6e19
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552276"
---
# <a name="auto-confirm-pattern"></a>Otomatik onaylama deseni
Bu örnek bir özel gösteren çalıştıran üç senaryoları oluşur `AutoConfirmScope` etkinlik. İlk örnek, bir dizi burada ikinci ve üçüncü iç içe içinde dört compensable etkinliği başarılı yürütme gösterir bir `AutoConfirmScope`. İkinci örnek, dördüncü yürütülmesini sonra oluşan bir özel durum ile aynı dizi gösterir. <xref:System.Activities.Statements.CompensableActivity>. Üçüncü senaryo gerçekleşen bir özel durum ile aynı dizi gösterir `AutoConfirmScope` saniye sonra <xref:System.Activities.Statements.CompensableActivity> tamamlar.  
  
 Örnek, tüm alt compensable etkinliklerin kapsamı işlemin başarıyla tamamlanmasından sonra nerede onaylanır auto-confirm desenini gösterir. Bu düzen, bunlar artık dengelenebilecek Onaylandı veya olarak tüm alt compensable etkinliklerin ömrünü tanımlar.  
  
 Kapsam oluşan bir <xref:System.Activities.Statements.TryCatch> burada <xref:System.Activities.Statements.TryCatch.Try%2A> bir iç <xref:System.Activities.Statements.CompensableActivity>. Kullanıcı tarafından belirtilen gövdesi `AutoConfirmScope` iç gövdesi <xref:System.Activities.Statements.CompensableActivity>. Bu iç zaman <xref:System.Activities.Statements.CompensableActivity> tamamlanır ürettiği bir <xref:System.Activities.Statements.CompensationToken> out-bağımsız değişken olarak. `AutoConfirmScope` Kullanan bir <xref:System.Activities.Statements.TryCatch.Finally%2A> belirteci bir olup oluşturulur ve iç onaylar sonra olup olmadığını denetlemek için <xref:System.Activities.Statements.CompensableActivity>. İç <xref:System.Activities.Statements.CompensableActivity> kendi gövdesinde bulunabilir compensable tüm etkinlikler için varsayılan Dengelemesi çağırır.  
  
 İlk senaryoda başarılı iş akışlarının yürütülmesini gösterir ve ikinci ve üçüncü compensable etkinlikleri iş akışı tamamlandıktan ve birinci ve dördüncü onaylanır zaten onaylanır gösterir. Bu üç, iki, dört ve bir onay sırasını oluşturur.  
  
 İkinci senaryoda, dört compensable etkinliği tamamladıktan sonra özel bir durum gösterilmektedir. Compensable etkinlikler iki ve üç zaten Onaylandı çünkü bunlar etkilenmez, ancak biri ve dört dengelenebilecek. Bu oluşturan üç onaylayın, iki onaylayın, dört dengelemek ve bir telafi.  
  
 Son senaryo başarısız yürütülmesini gösterir `AutoConfirmScope`. Bu senaryoda, ikinci tamamlanmasından sonra özel bir durum oluştuğunda <xref:System.Activities.Statements.CompensableActivity>. Üçüncü ve dördüncü compensable etkinlikleri yürütülmedi çünkü bunlar etkilenmez. Kapsam başarıyla tamamlanmadığı için ikinci <xref:System.Activities.Statements.CompensableActivity> doğrulanmadı. Bu oluşturur ve sonra iki tane maaş sırası.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], AutoConfirmSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`