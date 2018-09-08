---
title: Onaylama
ms.date: 03/30/2017
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
ms.openlocfilehash: caa712aa52da01ce44335a361fd6c9f5215316bf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132061"
---
# <a name="confirmation"></a>Onaylama
Bu örnek kullanımını çevreleyen dört ilgili yaygın senaryolar gösterilmektedir <xref:System.Activities.Statements.CompensableActivity> ve onay. Örnek onayı gösteren dört iş akışlarını çalıştırır. Bu örnek, bildirim temelli ve buyurgan sürümlerinde kullanılabilir.  
  
## <a name="confirm-a-compensable-activity"></a>Compensable etkinliğinde onaylayın  
 İlk iş akışınızı compensable etkinliğinde onaylayın yapmayı gösteren ve iki dizi oluşur <xref:System.Activities.Statements.CompensableActivity> örnekleri. İkinci tamamlanmasından sonra <xref:System.Activities.Statements.CompensableActivity> Onayla etkinliği ilk etkinliğini onaylıyor. İş akışı başarıyla tamamlandığında, tüm <xref:System.Activities.Statements.CompensableActivity> örnekleriyle dengelenebilecek veya onaylanan değil, varsayılan düzenini kullanarak otomatik olarak onaylanır. Onayla olmadan ikinci <xref:System.Activities.Statements.CompensableActivity> önce doğrulanmış.  
  
## <a name="explicit-compensation"></a>Açık maaş  
 İkinci senaryoda varsayılan onayını etkileyen gösterir, bir <xref:System.Activities.Statements.CompensableActivity> açıkça dengelendi. İş akışı dizisi iki oluşur <xref:System.Activities.Statements.CompensableActivity> ikinci ilk tamamlandıktan sonra etkinlikler açıkça dengelendi. Sonuç olarak iş akışı tamamlandığında yalnızca ikinci <xref:System.Activities.Statements.CompensableActivity> onaylanır.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>İç içe geçmiş CompensableActivity etkinlikler için onay sırasını denetleme  
 Üçüncü senaryo iç içe geçmiş onay sırasını denetlemek nasıl gösterir <xref:System.Activities.Statements.CompensableActivity>. Senaryo oluşan bir <xref:System.Activities.Statements.CompensableActivity> kökü olarak iş akışı. Kök gövdesi <xref:System.Activities.Statements.CompensableActivity> üç oluşan bir dizidir <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> Kök <xref:System.Activities.Statements.CompensableActivity> ilk ikinci iç içe geçmiş sonra onaylamak için belirten bir sıra <xref:System.Activities.Statements.CompensableActivity>. İş akışı tamamlandığında, kök onaylar <xref:System.Activities.Statements.CompensableActivity>, daha sonra ikinci ve üçüncü iç içe geçmiş ilk onaylar <xref:System.Activities.Statements.CompensableActivity>bu sırası. Sonuç olarak, varsayılan onay sıra temelde ters çevrilir. Çünkü üçüncü <xref:System.Activities.Statements.CompensableActivity> açıkça kök bir parçası olarak onaylanmadı <xref:System.Activities.Statements.CompensableActivity> tarafından <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, varsayılan sırasına göre onaylanır. Ancak, yalnızca olduğu için onaylanmamış <xref:System.Activities.Statements.CompensableActivity> bu yalnızca, Onaylandı anlamına gelir.  
  
## <a name="scoping-of-variables"></a>Değişkenlerinin kapsamı  
 Dördüncü senaryo değişkenlerin ömrünü nasıl tanımlanan gösterir bir <xref:System.Activities.Statements.CompensableActivity> veya ebeveynleri biridir hala kapsam <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> veya <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> işleyicileri yürütüldüğünde etkinliğin tamamlandı veya iş akışı sahip olsa bile tamamlandı. İş akışı dizisi iki oluşur <xref:System.Activities.Statements.CompensableActivity>. Birincisi, değişken gövdesinde `mySum` 5 ve 10 yazdırılan sonucu toplama ayarlanır. İkinci gövdesinde <xref:System.Activities.Statements.CompensableActivity>, sum mevcut sum ve 7 toplamı için ayarlanır ve sonucu yazdırılır. İlk özel işleyicisini tanımlanan <xref:System.Activities.Statements.CompensableActivity>, hangi toplamı yazdırır, 7 çıkarır ve toplamı yeniden yazdırır. Değişken yalnızca ikisinin gövdeleri için kapsamda olan yazdırılan SUM'ları inceleyerek boş olduğundan <xref:System.Activities.Statements.CompensableActivity> ancak <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  ConfirmationSample.exe uygulamayı çalıştırın.  
  
3.  Aşağıdaki çıktıyı inceleyin:  
  
 **Açık onayı: Başlangıç workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: workflowCompensableActivity2, onay HandlerEnd: onay HandlerExplicit maaş: başlangıcı workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: workflowCompensableActivity2, maaş HandlerEnd: onay HandlerCustom onay işleyicisi: başlangıcı workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: workflowCompensableActivity1, BodyEnd: onay HandlerCompensableActivity2: onay HandlerCompensableActivity3: bir onay işleyicisinde onay HandlerVariable erişim: WorkflowCompensableActivity1 başlangıcı: BodyCompensableActivity1: Toplam: 15CompensableActivity2: BodyCompensableActivity2: sumCompensableActivity2 ekleme 7: artık toplamıdır: workflowCompensableActivity2, 22End: onay HandlerCompensableActivity1: Onay HandlerCompensableActivity2: Toplam: 22CompensableActivity2: 12 çıkardıktan sonra artık toplamıdır: çıkmak için ENTER 10Press.**  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`