---
title: CancellationScope kullanma
ms.date: 03/30/2017
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
ms.openlocfilehash: 82d44fff869f207c09dc7685fc3470630e001a59
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731527"
---
# <a name="using-cancellationscope"></a>CancellationScope kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.CancellationScope> uygulamada işi iptal etmek için etkinlik.  
  
 İşlem iptal için bunları işlemek için iyi bilinen programlama yapısı birçok orta katman bileşen ve hizmetlere bağlıdır.  Ancak, bir işlemde yapılan iş iptal edilmesi gerekir birçok durum vardır.  İptal edilebilir iş ilk izlenmesi için İptal'i kullanarak işlemleri kullanmaktan daha zordur. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] Bu sağlayarak yardımcı olan bir <xref:System.Activities.Statements.CancellationScope> etkinlik.  
  
 İptal olabilir'nden ya da bir etkinlik içinde ya da etkinliğin üst tetiklendi.  Alt kendi üst etkinliği tarafından zamanlanır (gibi bir <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, ya da özel bir bileşik etkinliği).  Üst etkinliği, çocuk etkinliklerinin herhangi bir nedenle iptal edebilirsiniz.  Örneğin, bir <xref:System.Activities.Statements.Parallel> etkinlik üç alt dala sahip her bir dal tamamlanan kalan alt dalları iptal eder ve <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ifadeyi hesaplar için `true`. İş akışı dışarıdan konak uygulama tarafından çağırarak iptal edilebilir <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Kullanılacak <xref:System.Activities.Statements.CancellationScope> etkinliği içine iptal edilmesi gereken iş put <xref:System.Activities.Statements.CancellationScope.Body%2A> özelliği ve put iptali gerçekleştirilen iş <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> özelliği.  
  
 Bu örnek etkinlik içinde etkinliği iptal ediliyor gösterir.  
  
 Göstermek için örnek kullanır senaryo <xref:System.Activities.Statements.CancellationScope> olabildiğince çabuk Miami bilet satın almak isteyen bir istemci bir etkinliktir. İş istediğiniz iki seyahat kurumları vardır. İki örnek kullanır <xref:System.Activities.Statements.CancellationScope> içinde bir <xref:System.Activities.Statements.Parallel> bu iş mantığı modellemek için etkinlik. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> , <xref:System.Activities.Statements.Parallel> Etkinlik ayarlandığında `true`; <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> olan herhangi bir dal tamamlandıktan sonra iade, bu ilk dal tamamlandıktan sonra iptal edilecek kalan dal neden olur. İstemci uygulaması hem kurumları bilet satın almak için ister ve ilk bilet satın doğruladığında, uygulamanın diğer Ajans sırada iptal eder.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CancelationScopeXAML.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`