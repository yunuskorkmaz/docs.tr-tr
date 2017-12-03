---
title: CancellationScope kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2082ab8e0a9736cf56b7b551335ed57d082f7c8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-cancellationscope"></a>CancellationScope kullanma
Bu örnek nasıl kullanılacağı ortaya <xref:System.Activities.Statements.CancellationScope> bir uygulamada iş iptal etmek için etkinlik.  
  
 İyi bilinen programlama yapı bunları iptalleri işleme işlemlerinin çoğu orta katman bileşenlerini ve hizmetlerini kullanır.  Ancak, bir işlem içinde gerçekleştirilemez iş iptal edilmesi gerekir birçok durumlar vardır.  İptal edilmelidir iş ilk izlenmesi gerekir çünkü iptal kullanarak işlemleri kullanmaktan çok daha zordur. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]Bu sağlayarak yardımcı olan bir <xref:System.Activities.Statements.CancellationScope> etkinlik.  
  
 İptal olabilir herhangi birinden bir etkinlik veya etkinliğin üst tetiklendi.  Alt etkinlikler kendi üst etkinliği tarafından zamanlanmış (gibi bir <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, ya da özel bir bileşik etkinlik).  Üst etkinlik alt etkinliklerin herhangi bir nedenle iptal edebilirsiniz.  Örneğin, bir <xref:System.Activities.Statements.Parallel> bir dal tamamlanmadan zaman, üç alt dala sahip etkinliğini kalan alt dala iptal eder ve <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ifadeyi hesaplar için `true`. İş akışı dışarıdan konak uygulama tarafından çağırarak iptal edilebilir <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Kullanılacak <xref:System.Activities.Statements.CancellationScope> etkinlik, put içine iptal edilmesi gereken iş <xref:System.Activities.Statements.CancellationScope.Body%2A> özelliği ve put iptal sonra gerçekleştirilen iş <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> özelliği.  
  
 Bu örnek etkinlik etkinliği iptal ediliyor gösterir.  
  
 Örnek göstermek için kullandığı senaryo <xref:System.Activities.Statements.CancellationScope> Miami bilet hemen satın almak isteyen bir istemci bir etkinliktir. İş istediğiniz iki seyahat kurumları vardır. İki örnek kullanır <xref:System.Activities.Statements.CancellationScope> içinde bir <xref:System.Activities.Statements.Parallel> bu iş mantığı modellemek için etkinlik. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> , <xref:System.Activities.Statements.Parallel> Etkinlik ayarlanmış `true`; <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> olan herhangi bir dal tamamlandıktan sonra işaretli değilse, bu ilk şube tamamlandıktan sonra iptal edilmesi kalan şube neden olur. İstemci uygulaması bilet satın almak için her iki kurumları ister ve ilk bilet satın olduğunu onaylarsa, uygulamanın diğer Teşkilatı siparişe iptal eder.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CancelationScopeXAML.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`