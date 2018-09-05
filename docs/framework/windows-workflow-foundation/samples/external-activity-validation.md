---
title: Dış etkinlik doğrulama
ms.date: 03/30/2017
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
ms.openlocfilehash: 4805bec3deed0779b02687b11dd487e673802925
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527813"
---
# <a name="external-activity-validation"></a>Dış etkinlik doğrulama
Bu örnek, yazarı olmayan yerleşik bir etkinlik için doğrulama mantığı eklemenize gösterilmektedir. Doğrulama mantığını gerektirme oluşur tüm <xref:System.Activities.Statements.If> etkinlikleri sunmak ya da sahip iş akışında kendi <xref:System.Activities.Statements.If.Then%2A> özellik kümesi veya kendi <xref:System.Activities.Statements.If.Else%2A> özellik kümesi. Ayrıca, denetleme Doğrulama mantığı içerir. tüm <xref:System.Activities.Statements.Pick> etkinlikler iş akışında mevcut olan birden fazla dal ve durum bu değilse, bir uyarı oluşturulur.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek bir iş akışı örneği ile doğrulamak için her bir etkinlik oluşturur: <xref:System.Activities.Statements.If> etkinlik ve <xref:System.Activities.Statements.Pick> etkinlik. A <xref:System.Activities.Validation.Constraint> her doğrulama davranışını oluşturulur. Bu örnekte oluşturulan sınırlamalardır `ConstraintError_IfShouldHaveThenOrElse` ve `ConstraintWarning_PickHasOneBranch`. Ardından, bu kısıtlamaları eklenen `AdditionalConstraints` koleksiyonunu bir <xref:System.Activities.Validation.ValidationSettings> örneği. Son olarak, `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> yöntemi <xref:System.Activities.Validation.ActivityValidationServices> etkinlikler iş akışı ve sonuçları yazdırılmıştır konsola doğrulama, doğrulamak üzere çağrılır.  
  
> [!NOTE]
>  Herhangi bir etkinliği ilke kısıtlamaları ekleyebilirsiniz. Örneğin, bir ilkesi kısıtlaması için ekleyebileceğiniz bir <xref:System.Activities.Statements.Sequence> veya <xref:System.Activities.Statements.Parallel> etkinlik.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ExternalActivityValidation.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için Ctrl + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`