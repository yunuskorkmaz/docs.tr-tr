---
title: Temel etkinlik oluşturma
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: ade8187ca44a8182b55cf0f01e5bfe5a9a747255
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518382"
---
# <a name="basic-activity-composition"></a>Temel etkinlik oluşturma
Bu örnek, özel etkinlikler ve daha fazla özel etkinlikler oluşturmak için sistem tarafından sağlanan etkinlikleri oluşturma işlemini gösterir.  
  
 Anket etkinliğini kullanarak iş akışı soruların listesini ankete zamanlar ve ardından alınan yanıtların çıkarır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek, üç özel etkinlikler kullanır. `ReadLine` Basit <xref:System.Activities.NativeActivity> \<dizesi > oluşturan bir <xref:System.Activities.Bookmark> zamanlanmış ve ardından ayarlar `Return` <xref:System.Activities.OutArgument%601> hangi değere <xref:System.Activities.Bookmark> sürdürülür. `Prompt` olan bir <xref:System.Activities.Activity%601> \<dizesi > alan bir <xref:System.Activities.InArgument%601>< dize\> adlı `Text` ve yanıtta kullanıcıları döndürür `Result` <xref:System.Activities.OutArgument%601> \<dizesi >. `Prompt` Etkinliği kullanan <xref:System.Activities.Statements.Sequence> ve <xref:System.Activities.Statements.WriteLine> .NET Framework'ün bir parçası olarak gönderin ve ayrıca özel içerir etkinlikleri `ReadLine` kullanıcı girişi almak için etkinlik. Son Özel Etkinlik `Survey` etkinlik. Bu bir <xref:System.Activities.Activity>< ICollection\<dize >>.  Bu etkinlik alır bir <xref:System.Activities.InArgument%601>< IEnumerable < string\>> adlı `Questions` ve doldurur `Result` out bağımsız değişkeni ile yanıtlar. `Survey` Etkinliği kullanan <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> ve <xref:System.Activities.Statements.AddToCollection%601> gösteren ve .NET Framework `Prompt` anket sorular sorup yanıtlar almak için etkinlik.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Açık **BasicActivityComposition.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`