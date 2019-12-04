---
title: Native Etkinliği Kullanan Özel Bileşik
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 57c724ad55c3aa2960e9a2d11fcd8419a94a0c72
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715170"
---
# <a name="custom-composite-using-native-activity"></a>Native Etkinliği Kullanan Özel Bileşik
Bu örnek, bir iş akışının yürütülme akışını denetlemek için diğer <xref:System.Activities.Activity> nesneleri zamanlayan <xref:System.Activities.NativeActivity> nasıl yazılacağını gösterir. Bu örnek, bunun nasıl yapılacağını göstermek için iki ortak denetim akışı ve sırası kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar
 `MySequence`başlayarak, dikkat edilecek ilk şey, <xref:System.Activities.NativeActivity>türettiği şeydir. <xref:System.Activities.NativeActivity>, `Execute` yöntemine geçirilen <xref:System.Activities.NativeActivityContext> aracılığıyla iş akışı çalışma zamanının tam kapsamını kullanıma sunan <xref:System.Activities.Activity> nesnesidir.

 `MySequence`, iş akışı yazarı tarafından doldurulan <xref:System.Activities.Activity> nesnelerinin ortak bir koleksiyonunu kullanıma sunar. İş akışı yürütülmeden önce, iş akışı çalışma zamanı bir iş akışındaki her etkinlikte <xref:System.Activities.Activity.CacheMetadata%2A> yöntemini çağırır. Bu işlem sırasında, çalışma zamanı, veri kapsamı ve ömür yönetimi için üst-alt ilişkileri belirler. <xref:System.Activities.Activity.CacheMetadata%2A> yönteminin varsayılan uygulanması, <xref:System.Collections.IEnumerable>etkinliğinin alt öğeleri olarak <xref:System.Activities.Activity> veya \<<xref:System.Activities.Activity>> `MySequence` bir özelliği eklemek için `MySequence` etkinliğinin <xref:System.ComponentModel.TypeDescriptor> örnek sınıfını kullanır.

 Bir etkinlik, alt etkinliklerin ortak bir koleksiyonunu kullanıma sunışınızda, büyük olasılıkla bu alt etkinliklerin paylaştığı durumdur. Bu durumda üst etkinlik için en iyi uygulamadır çünkü bu durumda `MySequence`, alt etkinliklerin bu işlemi gerçekleştirebilecekleri bir dizi değişken koleksiyonunu da kullanıma sunar. Alt etkinlikler gibi <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi, <xref:System.Activities.Variable>etkinliğiyle ilişkili değişkenler olarak <xref:System.Activities.Variable> veya <xref:System.Collections.IEnumerable>\<> `MySequence` gibi ortak özellikler ekler.

 `MySequence`alt öğeleri tarafından yönetilen genel değişkenlerin yanı sıra, `MySequence` alt öğelerinin yürütüldüğü yerde de takip etmelidir. Bunu gerçekleştirmek için `currentIndex`özel bir değişken kullanır. Bu değişken, `MySequence` etkinliğinin <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi içindeki <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> yöntemine bir çağrı eklenerek `MySequence` ortamının bir parçası olarak kaydedilir. `MySequence` `Activities` koleksiyonuna eklenen <xref:System.Activities.Activity> nesneleri bu şekilde eklenen değişkenlere erişemez.

 Çalışma zamanı tarafından `MySequence` yürütüldüğünde, çalışma zamanı bir <xref:System.Activities.NativeActivityContext>geçirerek <xref:System.Activities.NativeActivity.Execute%2A> yöntemini çağırır. <xref:System.Activities.NativeActivityContext>, etkinliğin proxy 'si, bağımsız değişkenlerin ve değişkenlerin başvurusunun yanı sıra diğer <xref:System.Activities.Activity> nesneleri veya `ActivityDelegates`için yeniden çalışma zamanına geri gönderilir. `MySequence`, ilk alt öğenin ve sonraki tüm alt öğelerin tek bir yöntemde zamanlanması mantığını kapsüllemek için bir `InternalExecute` yöntemi kullanır. `currentIndex`başvurusu ile başlatılır. `Activities` koleksiyonundaki sayımla eşitse, sıra tamamlandığında, etkinlik herhangi bir çalışmayı zamanlamadan geri döner ve çalışma zamanı onu <xref:System.Activities.ActivityInstanceState.Closed> durumuna taşıdır. `currentIndex` etkinlik sayısından azsa, sonraki alt öğe `Activities` koleksiyonundan alınır ve <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>`MySequence` çağırır ve <xref:System.Activities.CompletionCallback> yöntemine işaret eden bir `InternalExecute` olur. Son olarak, `currentIndex` artırılır ve denetim çalışma zamanına geri getirilir. Bir `MySequence` örneği zamanlanmış bir alt <xref:System.Activities.Activity> nesnesine sahip olduğu sürece, çalışma zamanı bunu yürütme durumunda olacak şekilde değerlendirir.

 Alt etkinlik tamamlandığında <xref:System.Activities.CompletionCallback> yürütülür. Döngü üstten devam ediyor. `Execute`gibi, bir <xref:System.Activities.CompletionCallback> çalışma zamanına erişim sağlayan bir <xref:System.Activities.NativeActivityContext>alır.

 `MyWhile`, tek bir <xref:System.Activities.Activity> nesnesini sürekli olarak zamanlıyor ve bu zamanlamanın bir <xref:System.Activities.Activity%601>< bool\> bu zamanlamanın yapılıp yapılmayacağını anlamak için `Condition` adında `MySequence` farklıdır. `MySequence`gibi `MyWhile`, zamanlama mantığını merkezileştirmek için bir `InternalExecute` yöntemi kullanır. `Condition`<xref:System.Activities.Activity>< bool\>, <xref:System.Activities.CompletionCallback%601>adlı bir \<bool > ile zamanlar. `Condition` yürütülmesi tamamlandığında, sonucu, `result`adlı türü kesin belirlenmiş bir parametrede bu <xref:System.Activities.CompletionCallback> üzerinden kullanılabilir. `true`, `MyWhile` <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>çağırır, `Body`<xref:System.Activities.Activity> nesnesini ve `InternalExecute` <xref:System.Activities.CompletionCallback>. `Body` yürütülmesi tamamlandığında, `Condition` tekrar tekrar başlatarak `InternalExecute`yeniden zamanlanır. `Condition` `false`döndürdüğünde, bir `MyWhile` örneği, `Body` zamanlamaya gerek kalmadan çalışma zamanına denetim verir ve çalışma zamanı onu <xref:System.Activities.ActivityInstanceState.Closed> durumuna taşısalar.

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Visual Studio 2010 ' de bileşik. sln örnek çözümünü açın.

2. Çözümü derleyin ve çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
