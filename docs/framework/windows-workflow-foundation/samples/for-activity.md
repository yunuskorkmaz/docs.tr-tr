---
title: "Etkinlik için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3305defd4f2819a3ebe9d3b7429ddac11ae6833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="for-activity"></a>Etkinlik için
İçin örnek devralan bir özel etkinlik oluşturmak nasıl gösterir <xref:System.Activities.NativeActivity>ve gerçek dünya örneği yürütmek için bir iş akışında kullanın. C# gibi bu örnek işlevleri dahil özel etkinlik `for` deyimi. T  
  
 `For` Özel etkinlik adında özelliklere sahip `InitAction`, `IterationAction`, `Condition`, ve `Body` başlatma deyimi, yinelemeli deyimi, devamlılık koşul karşılık gelir ve deyimi sırasıyla gövde Standart C# içinde bulunan `For` deyimi.  
  
 Aşağıdaki tabloda örnek anahtar dosyaları açıklanmaktadır.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|For.cs|Sınıf tanımı `For` genişletir özel etkinlik <xref:System.Activities.NativeActivity> C# işlevselliğini sağlamak için sınıf `For` deyimi.|  
|Program.cs|Özel kullanarak bir koleksiyon temel yinelemeli çalışmayı gerçekleştiren bir istemci uygulaması `For` etkinlik.|  
  
> [!NOTE]
>  Kullanırken `For` özel etkinlik emin `Condition` özelliği ayarlanmış; Aksi takdirde sonsuz bir döngüde oluşabilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Devralan bir özel etkinlik oluşturmak <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Tartışma  
 Aşağıdaki tabloda bu örnekte dahil etkinlik özelliklerini açıklar.  
  
 InitAction  
 Başlatma deyimi  
  
 IterationAction  
 Yinelemeli deyimi  
  
 Koşul  
 Devamlılık deyimi  
  
 Gövde  
 Gövde deyimi  
  
 Etkinlik devraldığı <xref:System.Activities.NativeActivity> çalıştırmak için ek etkinlikler zamanlama gibi çalışma zamanı özellikleri birini kullanarak erişmek için `ScheduleActivity` yöntemlerini <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], For.sln çözüm dosyasını açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  F5 tuşuna basarak çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`