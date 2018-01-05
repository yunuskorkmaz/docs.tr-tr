---
title: "Dış etkinlik doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da326969e622a51f6a93b9faf5f81da079ea4003
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="external-activity-validation"></a>Dış etkinlik doğrulama
Bu örnek nasıl doğrulama mantığını yazarı olmayan yerleşik bir etkinlik ekleneceğini gösterir. Doğrulama mantığını zorlama oluşur tüm <xref:System.Activities.Statements.If> etkinlikleri sunmak ya da iş akışında kendi <xref:System.Activities.Statements.If.Then%2A> özellik kümesi veya kendi <xref:System.Activities.Statements.If.Else%2A> özellik kümesi. Ayrıca, doğrulama mantığını olduğunu denetimini içermektedir ve tüm <xref:System.Activities.Statements.Pick> etkinlikler iş akışında mevcut sahip birden çok dal ve bu durumda değilse, bir uyarı üretilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek bir iş akışı doğrulamak için her etkinlik bir örneğini oluşturur: <xref:System.Activities.Statements.If> etkinlik ve <xref:System.Activities.Statements.Pick> etkinlik. A <xref:System.Activities.Validation.Constraint> her doğrulama davranışını oluşturulur. Bu örnekte oluşturulan sınırlamalardır `ConstraintError_IfShouldHaveThenOrElse` ve `ConstraintWarning_PickHasOneBranch`. Ardından, bu kısıtlamaların eklenir `AdditionalConstraints` koleksiyonu bir <xref:System.Activities.Validation.ValidationSettings> örneği. Son olarak, `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> yöntemi <xref:System.Activities.Validation.ActivityValidationServices> iş akışı ve sonuçları yazdırılmıştır konsola doğrulama etkinlikler doğrulamak üzere çağrılır.  
  
> [!NOTE]
>  İlke kısıtlamaları için herhangi bir etkinlik ekleyebilirsiniz. Örneğin, bir ilke kısıtlaması ekleyebileceğiniz bir <xref:System.Activities.Statements.Sequence> veya <xref:System.Activities.Statements.Parallel> etkinlik.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ExternalActivityValidation.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için Ctrl + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`