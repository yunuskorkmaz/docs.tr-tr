---
title: Temel etkinlik oluşturma
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: 67cdad30c60ebbeaf546d7086c6e895fa49a51c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515710"
---
# <a name="basic-activity-composition"></a>Temel etkinlik oluşturma
Bu örnek özel etkinlikler ve daha fazla özel etkinlikler oluşturmak için sistem tarafından sağlanan etkinlikleri oluşturmak nasıl gösterir.  
  
 Anket etkinliğini kullanarak iş akışı bir soru listesi ile anket zamanlar ve alınan yanıtların çıkarır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek, üç özel etkinlikler kullanmaktadır. `ReadLine` Basit bir olan <xref:System.Activities.NativeActivity> \<dize > oluşturan bir <xref:System.Activities.Bookmark> zamanlanmış ve ardından ayarlar `Return` <xref:System.Activities.OutArgument%601> hangi değerine <xref:System.Activities.Bookmark> sürdürülür. `Prompt` olan bir <xref:System.Activities.Activity%601> \<dize > alan bir <xref:System.Activities.InArgument%601>< dize\> adlı `Text` ve kullanıcıların yanıt olarak döndürür `Result` <xref:System.Activities.OutArgument%601> \<dize >. `Prompt` Aktivitesi kullanır <xref:System.Activities.Statements.Sequence> ve <xref:System.Activities.Statements.WriteLine> sevk .NET Framework'ün bir parçası olarak ve ayrıca özel bir araya getirir etkinlikleri `ReadLine` kullanıcı girişi alma etkinliği. Son özel etkinliği `Survey` etkinlik. Bu bir <xref:System.Activities.Activity>< ICollection\<dize >>.  Bu etkinliği alır bir <xref:System.Activities.InArgument%601>< IEnumerable < dize\>> adlı `Questions` ve doldurur `Result` out yanıtlarla bağımsız değişkeni. `Survey` Aktivitesi kullanır <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> ve <xref:System.Activities.Statements.AddToCollection%601> .NET Framework ve uygular `Prompt` anket sorular sormak ve yanıtları almak için etkinlik.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Açık **BasicActivityComposition.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`