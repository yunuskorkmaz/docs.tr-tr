---
title: Native Etkinliği Kullanan Özel Bileşik
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 2b922ef721ab4d125f390e908eb8ea4d3b087035
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142803"
---
# <a name="custom-composite-using-native-activity"></a>Native Etkinliği Kullanan Özel Bileşik
Bu örnek, iş akışının yürütülmesinin <xref:System.Activities.Activity> akışını denetlemek için diğer nesneleri zamanlayan bir <xref:System.Activities.NativeActivity> yazmanın nasıl yapılacağını gösterir. Bu örnek, bunun nasıl yapılacağını göstermek için sıralı ve While olmak üzere iki ortak denetim akışı kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Ile `MySequence`başlayarak , fark etmek için ilk <xref:System.Activities.NativeActivity>şey, bu türetilmiştir . <xref:System.Activities.NativeActivity>yönteme <xref:System.Activities.Activity> <xref:System.Activities.NativeActivityContext> geçirilen aracılığıyla iş akışı çalışma süresinin tam genişliğini ortaya çıkaran nesnedir. `Execute`

 `MySequence`iş akışı yazarı <xref:System.Activities.Activity> tarafından doldurulan nesnelerin ortak bir koleksiyonunu ortaya çıkarır. İş akışı yürütülmeden önce, iş <xref:System.Activities.Activity.CacheMetadata%2A> akışı çalışma zamanı, iş akışındaki her etkinlikteki yöntemi çağırır. Bu işlem sırasında, çalışma süresi veri kapsam belirleme ve yaşam boyu yönetimi için üst-alt ilişkileri kurar. <xref:System.Activities.Activity.CacheMetadata%2A> Yöntemin varsayılan uygulaması, <xref:System.ComponentModel.TypeDescriptor> <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity> `MySequence` etkinliğin alt `MySequence` ları olarak tür <xref:System.Activities.Activity> veya> herhangi bir kamu özelliği eklemek için etkinlik için örnek sınıf kullanır.

 Bir etkinlik, bir genel alt etkinlik koleksiyonunu ortaya çıkardığında, bu alt etkinliklerin durumu paylaşması olasıdır. Bu durumda, `MySequence`alt etkinliklerin bunu başarabileceği değişkenler koleksiyonunu da ortaya çıkarmak, üst etkinlik için en iyi uygulamadır. Alt etkinlikler gibi, <xref:System.Activities.Activity.CacheMetadata%2A> yöntem tür <xref:System.Activities.Variable> veya <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> ortak özellikleri `MySequence` etkinlik ile ilişkili değişkenler olarak ekler.

 Çocuklar tarafından manipüle edilen kamusal değişkenlerin `MySequence`yanı `MySequence` sıra, çocuklarının infazında nerede olduğunu da takip etmelidir. Bunu başarmak için `currentIndex`özel bir değişken kullanır. Bu değişken, `MySequence` etkinlik <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> `MySequence` <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi içinde yönteme bir çağrı eklenerek ortamın bir parçası olarak kaydedilir. Koleksiyona <xref:System.Activities.Activity> `MySequence` eklenen nesneler bu şekilde eklenen değişkenlere erişemez. `Activities`

 Çalışma `MySequence` zamanı tarafından yürütüldüğünde, çalışma <xref:System.Activities.NativeActivity.Execute%2A> zamanı yöntemini <xref:System.Activities.NativeActivityContext>çağırır ve bir . Etkinlik <xref:System.Activities.NativeActivityContext> proxy'si, bağımsız değişkenleri ve değişkenleri dereferencing ve diğer <xref:System.Activities.Activity> nesneleri zamanlama `ActivityDelegates`veya . `MySequence`ilk `InternalExecute` alt ve sonraki tüm alt çocukları tek bir yöntemde zamanlama mantığını özetlemek için bir yöntem kullanır. Bu dereferencing ile `currentIndex`başlar . `Activities` Koleksiyondaki sayıma eşitse, sıra tamamlanır, etkinlik herhangi bir çalışma zamanlamadan döndürür ve <xref:System.Activities.ActivityInstanceState.Closed> çalışma zamanı onu duruma taşır. Etkinlik `currentIndex` sayısı nın daha az olması durumunda, bir `Activities` sonraki `MySequence` çocuk <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>koleksiyondan elde edilir ve <xref:System.Activities.CompletionCallback> çağrılar , `InternalExecute` zamanlanacak çocuk ta geçerken ve yönteme işaret eden bir çocuk. Son olarak, artış `currentIndex` ve denetim çalışma süresine geri verilir. Bir alt <xref:System.Activities.Activity> nesnenin `MySequence` zamanlanması gerektiği sürece, çalışma zamanı bunu Yürütme durumunda olarak kabul eder.

 Alt etkinlik tamamlandığında, yürütülür. <xref:System.Activities.CompletionCallback> Döngü yukarıdan devam ediyor. Gibi `Execute`, <xref:System.Activities.CompletionCallback> a <xref:System.Activities.NativeActivityContext>alır , uygulayıcısı çalışma süresine erişim veren.

 `MyWhile``MySequence` tek <xref:System.Activities.Activity> bir nesneyi tekrar tekrar zamanlaması ve bu zamanlamanın gerçekleşip gerçekleşmemesi gerektiğini belirlemek için<bir <xref:System.Activities.Activity%601> bool\> kullanması `Condition` açısından farklıdır. Gibi `MySequence` `MyWhile` , `InternalExecute` zamanlama mantığını merkezileştirmek için bir yöntem kullanır. `Condition` <xref:System.Activities.Activity> Bu adlı `OnEvaluationCompleted`bir\> <xref:System.Activities.CompletionCallback%601> \<bool> ile<bool programları . Yürütme `Condition` tamamlandığında, sonucu bu <xref:System.Activities.CompletionCallback> aracılığıyla güçlü bir şekilde yazılan parametre de `result`. Eğer `true` `MyWhile` , <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>çağırır , `Body` <xref:System.Activities.Activity> nesne `InternalExecute` ve <xref:System.Activities.CompletionCallback>olarak geçen . Yürütme `Body` tamamlandığında, `Condition` döngüyü yeniden `InternalExecute`başlatırken yeniden zamanlanır. `Condition` Döndürdüğünde, `false`bir `MyWhile` örnek zamanlama olmadan denetimi çalışma süresine geri verir `Body` ve <xref:System.Activities.ActivityInstanceState.Closed> çalışma zamanı onu duruma taşır.

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Visual Studio 2010'da Composite.sln örnek çözümlerini açın.

2. Çözümü derleyin ve çalıştırın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
