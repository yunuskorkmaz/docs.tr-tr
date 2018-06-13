---
title: Etkinlik için
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: c79f295e7880f845c606a55f9c56ad65350f9c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515451"
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`