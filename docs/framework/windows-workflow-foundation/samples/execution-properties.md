---
title: Yürütme özellikleri
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748200"
---
# <a name="execution-properties"></a>Yürütme özellikleri
Bu örnek, bir yürütme özelliği özel bir etkinlikte kullanmadan nasıl gösterir. Bu örnekte, yürütme özelliği konsolun ön plan rengini belirler. Bir örnek iş akışı yürütme mantıksal nasıl farklı yolları gösterir (dallar, bir <xref:System.Activities.Statements.Parallel> etkinlik) aralıklı yürütme etkinlikleri rağmen farklı konsol renkleri koruyabilirsiniz (dalları arasında <xref:System.Activities.Statements.Parallel> etkinliği).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  ExecutionProperties.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Çözümü oluşturmadan önce ThreeColors.xaml görüntüleme, kullanılan özel etkinlikler çözümü olarak aynı anda oluşturulması gereken olduğundan bir hata görüntüler.  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`