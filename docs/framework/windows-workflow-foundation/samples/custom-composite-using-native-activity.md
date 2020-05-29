---
title: Native Etkinliği Kullanan Özel Bileşik
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: bf2b8123619df8977b0687c72663c6b482e35654
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200868"
---
# <a name="custom-composite-using-native-activity"></a>Native Etkinliği Kullanan Özel Bileşik
Bu örnek <xref:System.Activities.NativeActivity> <xref:System.Activities.Activity> , bir iş akışının yürütülme akışını denetlemek için diğer nesneleri zamanlayan bir nasıl yazılacağını gösterir. Bu örnek, bunun nasıl yapılacağını göstermek için iki ortak denetim akışı ve sırası kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Sürümünden itibaren `MySequence` , dikkat edilecek ilk şey, öğesinden türetilmedir <xref:System.Activities.NativeActivity> . <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity> yöntemine geçirilen iş akışı çalışma zamanının tam kapsamını kullanıma sunan nesnedir <xref:System.Activities.NativeActivityContext> `Execute` .

 `MySequence`<xref:System.Activities.Activity>iş akışı yazarı tarafından doldurulan bir nesne genel koleksiyonunu ortaya koyar. İş akışı yürütülmeden önce, iş akışı çalışma zamanı <xref:System.Activities.Activity.CacheMetadata%2A> bir iş akışındaki her etkinlikte yöntemini çağırır. Bu işlem sırasında, çalışma zamanı, veri kapsamı ve ömür yönetimi için üst-alt ilişkileri belirler. Yönteminin varsayılan uygulanması, etkinliğin <xref:System.Activities.Activity.CacheMetadata%2A> <xref:System.ComponentModel.TypeDescriptor> `MySequence` <xref:System.Activities.Activity> <xref:System.Collections.IEnumerable> \<<xref:System.Activities.Activity> alt öğesi olarak tür veya> ortak bir özelliğini eklemek için etkinliğin örnek sınıfını kullanır `MySequence` .

 Bir etkinlik, alt etkinliklerin ortak bir koleksiyonunu kullanıma sunışınızda, büyük olasılıkla bu alt etkinliklerin paylaştığı durumdur. Bu durumda üst etkinlik için en iyi uygulamadır çünkü bu durumda `MySequence` , alt etkinliklerin bunu gerçekleştirebilecekleri bir değişken koleksiyonunu da kullanıma sunar. Alt etkinlikler gibi yöntem, <xref:System.Activities.Activity.CacheMetadata%2A> <xref:System.Activities.Variable> <xref:System.Collections.IEnumerable> \<<xref:System.Activities.Variable> etkinlik ile ilişkili değişkenler olarak tür veya> ortak özellikleri ekler `MySequence` .

 Alt öğeleri tarafından yönetilen ortak değişkenlerin yanı sıra `MySequence` , `MySequence` alt öğelerinin yürütüldüğü yeri de takip etmelidir. Bunu gerçekleştirmek için özel bir değişken kullanır `currentIndex` . Bu değişken, `MySequence` <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> etkinliğin yöntemi içindeki yöntemine bir çağrı eklenerek ortamın bir parçası olarak kaydedilir `MySequence` <xref:System.Activities.Activity.CacheMetadata%2A> . <xref:System.Activities.Activity>Koleksiyona eklenen nesneler `MySequence` `Activities` Bu şekilde eklenen değişkenlere erişemez.

 `MySequence`Çalışma zamanı tarafından yürütüldüğünde, çalışma zamanı yöntemini çağırır ve ' a <xref:System.Activities.NativeActivity.Execute%2A> geçer <xref:System.Activities.NativeActivityContext> . , <xref:System.Activities.NativeActivityContext> Etkinliğin proxy 'si, bağımsız değişkenlerin ve değişkenlerin başvurusunun yanı sıra diğer nesneleri veya zamanlama için çalışma zamanına geri gönderilir <xref:System.Activities.Activity> `ActivityDelegates` . `MySequence``InternalExecute`tek bir yöntemde ilk alt öğe ve sonraki tüm alt öğeleri zamanlama mantığını kapsüllemek için bir yöntem kullanır. Öğesine başvuru yaparak başlar `currentIndex` . Koleksiyondaki sayıma eşitse `Activities` , sıra işlemi, etkinlik herhangi bir işi zamanlamaya gerek kalmadan döner ve çalışma zamanı onu <xref:System.Activities.ActivityInstanceState.Closed> duruma getirir. Etkinlik sayısından `currentIndex` daha azsa, sonraki alt öğe `Activities` koleksiyon ve `MySequence` çağrılardan elde edilir <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> , bu, zamanlanacak alt öğe ve <xref:System.Activities.CompletionCallback> yöntemi işaret eder `InternalExecute` . Son olarak, `currentIndex` artırılır ve denetim çalışma zamanına geri getirilir. Öğesinin bir `MySequence` alt <xref:System.Activities.Activity> nesnesi zamanlanmış olduğu sürece, çalışma zamanı bunu yürütme durumunda olacak şekilde değerlendirir.

 Alt etkinlik tamamlandığında, <xref:System.Activities.CompletionCallback> yürütülür. Döngü üstten devam ediyor. Benzer şekilde `Execute` ,, <xref:System.Activities.CompletionCallback> <xref:System.Activities.NativeActivityContext> çalışma zamanına erişim sağlayan bir alır.

 `MyWhile``MySequence`, tek bir nesneyi sürekli olarak zamanlıyor <xref:System.Activities.Activity> ve <xref:System.Activities.Activity%601> \> Bu, `Condition` bu zamanlamanın olup olmayacağını belirlemekte<bool olarak adlandırılan bir bool ' ı kullandığından farklıdır. Benzer `MySequence` `MyWhile` `InternalExecute` şekilde, zamanlama mantığını merkezileştirmek için bir yöntem kullanır. `Condition` <xref:System.Activities.Activity><bool değerini \> adlandırılmış bir ile zamanlar <xref:System.Activities.CompletionCallback%601> \<bool> `OnEvaluationCompleted` . Yürütmesi `Condition` tamamlandığında, bunun sonucu, <xref:System.Activities.CompletionCallback> adında türü kesin belirlenmiş bir parametre ile kullanılabilir hale gelir `result` . Eğer `true` , öğesini `MyWhile` çağırır <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> , öğesini `Body` <xref:System.Activities.Activity> ve olarak geçirerek `InternalExecute` <xref:System.Activities.CompletionCallback> . Yürütmesi `Body` tamamlandığında, `Condition` içinde yeniden zamanlanır ve `InternalExecute` döngü tekrar başlar. `Condition` `false` ' İ döndüğünde, bir örneği `MyWhile` , zamanlamayı zamanlamadan çalışma zamanına bir denetim verir `Body` ve çalışma zamanı onu duruma getirir <xref:System.Activities.ActivityInstanceState.Closed> .

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Visual Studio 2010 ' de bileşik. sln örnek çözümünü açın.

2. Çözümü derleyin ve çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
