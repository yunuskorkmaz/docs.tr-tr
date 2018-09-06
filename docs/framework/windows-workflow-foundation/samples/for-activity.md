---
title: Etkinlik için
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881530"
---
# <a name="for-activity"></a>Etkinlik için
Devralınan özel etkinlik oluşturma için örnek gösterir <xref:System.Activities.NativeActivity>ve bir iş akışında bir gerçek dünya örneği çalıştırmak için kullanın. Bu örnek işlevleri gibi C# içindeki özel etkinlik `for` deyimi. T  
  
 `For` Özel etkinlik adında özelliklere sahip `InitAction`, `IterationAction`, `Condition`, ve `Body` başlatma ifadesi, yinelemeli deyimi, devamlılık koşul karşılık gelir ve sırasıyla deyimi gövdesi Standart C# içinde bulunan `For` deyimi.  
  
 Aşağıdaki tabloda, örnekteki anahtar dosyalarını açıklar.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|For.cs|Sınıf tanımı `For` genişletir özel etkinlik <xref:System.Activities.NativeActivity> C# işlevlerini sağlar sınıfını `For` deyimi.|  
|Program.cs|Özel kullanarak bir koleksiyon üzerinde temel yineleme işini gerçekleştiren bir istemci uygulaması `For` etkinlik.|  
  
> [!NOTE]
>  Kullanırken `For` özel etkinlik emin `Condition` özelliği; Aksi takdirde sonsuz bir döngüye oluşabilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Devralınan özel etkinlik oluşturma <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Tartışma  
 Aşağıdaki tabloda, bu örnekte bulunan etkinlik özelliklerini açıklar.  
  
 InitAction  
 Başlatma ifadesi  
  
 IterationAction  
 Yinelemeli deyimi  
  
 Koşul  
 Devamlılık deyimi  
  
 Gövde  
 Gövde ifadesi  
  
 Etkinlik öğesinden devralınan <xref:System.Activities.NativeActivity> birini kullanarak çalıştırmak için ek etkinlikler zamanlamak gibi çalışma zamanı özelliklere erişim kazanmak için `ScheduleActivity` yöntemlerinin <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], For.sln çözüm dosyasını açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  F5 tuşuna basarak çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`