---
title: Onaylama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a686a07ed41aafd476dbb1934c178558d90d948
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="confirmation"></a>Onaylama
Bu örnek kullanımını çevreleyen dört yaygın senaryolar gösterilmektedir <xref:System.Activities.Statements.CompensableActivity> ve onay. Örnek onay göstermek için dört iş akışlarını çalıştırır. Bu örnek, bildirim temelli ve kesinlik temelli sürümlerinde kullanılabilir.  
  
## <a name="confirm-a-compensable-activity"></a>Compensable etkinliğini onaylayın  
 İlk iş akışı compensable etkinliğini onaylamak gösterilmiştir ve iki bir dizi oluşur <xref:System.Activities.Statements.CompensableActivity> örnekleri. İkinci tamamlanmasından sonra <xref:System.Activities.Statements.CompensableActivity> Onayla etkinlik ilk etkinlik onaylar. İş akışı başarıyla tamamlandığında, tüm <xref:System.Activities.Statements.CompensableActivity> dengelendi veya onaylanan değil örnekleri, varsayılan düzenini kullanarak otomatik olarak onaylanır. Onayla olmadan ikinci <xref:System.Activities.Statements.CompensableActivity> önce doğrulanmış.  
  
## <a name="explicit-compensation"></a>Açık maaş  
 İkinci senaryo varsayılan onayını etkileyen gösterir, bir <xref:System.Activities.Statements.CompensableActivity> açıkça dengelendi. İş akışı iki bir dizi oluşur <xref:System.Activities.Statements.CompensableActivity> ikinci ilk tamamlandıktan sonra etkinlikler açıkça dengelendi. Sonuç olarak, iş akışı tamamlandığında yalnızca ikinci <xref:System.Activities.Statements.CompensableActivity> doğrulanır.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>İç içe geçmiş CompensableActivity etkinlikler için onay sırasını denetleme  
 Üçüncü senaryo iç içe geçmiş onay sırasını denetimi gösterilmektedir <xref:System.Activities.Statements.CompensableActivity>. Senaryo oluşan bir <xref:System.Activities.Statements.CompensableActivity> iş akışı kökü olarak. Kök gövdesi <xref:System.Activities.Statements.CompensableActivity> üç dizisidir <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> Kök <xref:System.Activities.Statements.CompensableActivity> ikinci iç içe geçmiş sonra ilk onaylamak için belirten bir sırası <xref:System.Activities.Statements.CompensableActivity>. İş akışı tamamlandığında kök onaylar <xref:System.Activities.Statements.CompensableActivity>, ikinci ve üçüncü iç içe geçmiş ilk, o onaylar <xref:System.Activities.Statements.CompensableActivity>bu sırası. Sonuç olarak, varsayılan onay sıra temelde ters çevrilir. Çünkü üçüncü <xref:System.Activities.Statements.CompensableActivity> açıkça kök bir parçası olarak onaylanmadı <xref:System.Activities.Statements.CompensableActivity> tarafından <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, varsayılan sırasına göre doğrulanır. Ancak, çünkü tek onaylanmamış <xref:System.Activities.Statements.CompensableActivity> bu yalnızca Onaylandı anlamına gelir.  
  
## <a name="scoping-of-variables"></a>Değişkenleri kapsamı  
 Değişkenleri ömrü nasıl tanımlanmış dördüncü senaryo gösterilmektedir bir <xref:System.Activities.Statements.CompensableActivity> veya üst biri hala kapsam <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> veya <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> işleyicileri etkinliği tamamlanan veya iş akışının sahip olsa bile çalıştırılır tamamlandı. İş akışı iki bir dizi oluşur <xref:System.Activities.Statements.CompensableActivity>. Değişken ilk gövdesinde `mySum` 5, 10 ve yazdırılan sonuç toplamına ayarlanır. İkinci gövdesinde <xref:System.Activities.Statements.CompensableActivity>, sum toplamına mevcut sum ve 7 ayarlanır ve sonucu yazdırılan. Özel doğrulama işleyicisi ilk tanımlanan <xref:System.Activities.Statements.CompensableActivity>, hangi toplamı yazdırır, 7 çıkarır ve toplamı yeniden yazdırır. Yalnızca her ikisi de gövdeleri kapsamına değişkeni olan yazdırılan SUM'ları inceleyerek Temizle <xref:System.Activities.Statements.CompensableActivity> ancak <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  ConfirmationSample.exe uygulamayı çalıştırın.  
  
3.  Aşağıdaki çıktıyı inceleyin:  
  
 **Açık onay: başlangıcı workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: workflowCompensableActivity2, onay HandlerEnd: onay HandlerExplicit maaş: başlangıcı workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: workflowCompensableActivity2, maaş HandlerEnd: onay HandlerCustom onay işleyici: başlangıcı workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: workflowCompensableActivity1 BodyEnd: onay HandlerCompensableActivity2: onay HandlerCompensableActivity3: onay işleyicisinde onay HandlerVariable erişim: WorkflowCompensableActivity1 başlangıcı: BodyCompensableActivity1: toplamıdır: 15CompensableActivity2: BodyCompensableActivity2: sumCompensableActivity2 7 ekleme: artık toplamıdır: workflowCompensableActivity2 22End: onayı HandlerCompensableActivity1: Onay HandlerCompensableActivity2: toplamıdır: 22CompensableActivity2: 12 çıkardıktan sonra şimdi toplamıdır: çıkmak için 10Press girin.**  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`