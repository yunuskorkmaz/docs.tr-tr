---
title: Native Etkinliği Kullanan Özel Bileşik
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 8a0d1077c058ecdbad10a2e7bd61ff5eb75e1cb5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044318"
---
# <a name="custom-composite-using-native-activity"></a>Native Etkinliği Kullanan Özel Bileşik
Bu örnek, bir iş akışının yürütülme <xref:System.Activities.NativeActivity> akışını denetlemek için <xref:System.Activities.Activity> diğer nesneleri zamanlayan bir nasıl yazılacağını gösterir. Bu örnek, bunun nasıl yapılacağını göstermek için iki ortak denetim akışı ve sırası kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar
 <xref:System.Activities.NativeActivity>Sürümünden itibaren ,dikkatedilecekilkşey,öğesinden`MySequence`türetilmedir. <xref:System.Activities.NativeActivity>, yöntemine geçirilen iş akışı çalışma zamanının <xref:System.Activities.Activity> <xref:System.Activities.NativeActivityContext> tam kapsamını kullanıma sunan nesnedir. `Execute`

 `MySequence`iş akışı yazarı tarafından doldurulan <xref:System.Activities.Activity> bir nesne genel koleksiyonunu ortaya koyar. İş akışı yürütülmeden önce, iş akışı çalışma zamanı bir iş <xref:System.Activities.Activity.CacheMetadata%2A> akışındaki her etkinlikte yöntemini çağırır. Bu işlem sırasında, çalışma zamanı, veri kapsamı ve ömür yönetimi için üst-alt ilişkileri belirler. <xref:System.Activities.Activity.CacheMetadata%2A> <xref:System.Activities.Activity> Yönteminin varsayılan<xref:System.ComponentModel.TypeDescriptor>uygulamasında , bir veya >ortak\<özelliğini, öğesinin alt öğesi olarak <xref:System.Collections.IEnumerable> `MySequence` <xref:System.Activities.Activity> `MySequence` etkinlik.

 Bir etkinlik, alt etkinliklerin ortak bir koleksiyonunu kullanıma sunışınızda, büyük olasılıkla bu alt etkinliklerin paylaştığı durumdur. Bu durumda üst etkinlik için en iyi uygulamadır çünkü bu durumda `MySequence`, alt etkinliklerin bunu gerçekleştirebilecekleri bir değişken koleksiyonunu da kullanıma sunar. Alt <xref:System.Activities.Activity.CacheMetadata%2A> etkinlikler gibi yöntem, <xref:System.Activities.Variable> <xref:System.Activities.Variable> \< <xref:System.Collections.IEnumerable> etkinlik`MySequence` ile ilişkili değişkenler olarak tür veya > ortak özellikleri ekler.

 Alt öğeleri `MySequence`tarafından yönetilen ortak değişkenlerin yanı sıra, `MySequence` alt öğelerinin yürütüldüğü yeri de takip etmelidir. Bunu gerçekleştirmek için özel bir değişken `currentIndex`kullanır. Bu değişken, `MySequence` `MySequence` etkinliğin <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> yöntemi<xref:System.Activities.Activity.CacheMetadata%2A> içindeki yöntemine bir çağrı eklenerek ortamın bir parçası olarak kaydedilir. Koleksiyona eklenen <xref:System.Activities.Activity> `MySequence` nesneler bu şekilde eklenen değişkenlere erişemez. `Activities`

 Çalışma zamanı tarafından yürütüldüğünde, çalışma zamanı <xref:System.Activities.NativeActivity.Execute%2A> <xref:System.Activities.NativeActivityContext>yöntemini çağırır ve ' a geçer. `MySequence` , <xref:System.Activities.NativeActivityContext> Etkinliğin proxy 'si, bağımsız değişkenlerin ve değişkenlerin başvurusunun yanı sıra diğer <xref:System.Activities.Activity> nesneleri veya `ActivityDelegates`zamanlama için çalışma zamanına geri gönderilir. `MySequence`tek bir `InternalExecute` yöntemde ilk alt öğe ve sonraki tüm alt öğeleri zamanlama mantığını kapsüllemek için bir yöntem kullanır. Öğesine başvuru `currentIndex`yaparak başlar. `Activities` Koleksiyondaki sayıma eşitse, sıra işlemi, etkinlik herhangi bir işi zamanlamaya gerek kalmadan döner ve çalışma zamanı onu <xref:System.Activities.ActivityInstanceState.Closed> duruma getirir. <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> `MySequence` `Activities` <xref:System.Activities.CompletionCallback> `InternalExecute` Etkinlik sayısından daha azsa, sonraki alt öğe koleksiyon ve çağrılardan elde edilir, bu, zamanlanacak alt öğe ve `currentIndex` yöntemidir. `currentIndex` Son olarak, artırılır ve denetim çalışma zamanına geri getirilir. Öğesinin `MySequence` bir alt <xref:System.Activities.Activity> nesnesi zamanlanmış olduğu sürece, çalışma zamanı bunu yürütme durumunda olacak şekilde değerlendirir.

 Alt etkinlik tamamlandığında <xref:System.Activities.CompletionCallback> , yürütülür. Döngü üstten devam ediyor. Benzer `Execute` <xref:System.Activities.NativeActivityContext> şekilde<xref:System.Activities.CompletionCallback> ,, çalışma zamanına erişim sağlayan bir alır.

 `MyWhile``Condition` \> <xref:System.Activities.Activity%601>, tek <xref:System.Activities.Activity> bir nesneyi sürekli olarak zamanlıyor ve bu, bu zamanlamanın olup olmayacağını belirlemekte < bool olarak adlandırılan bir bool ' ı kullandığından farklıdır. `MySequence` Benzer `MySequence`şekilde `MyWhile` , zamanlama `InternalExecute` mantığını merkezileştirmek için bir yöntem kullanır. <xref:System.Activities.Activity>< Bool <xref:System.Activities.CompletionCallback%601> `Condition`değeriniadlı bool>\<ile zamanlar. `OnEvaluationCompleted`\> Yürütmesi `Condition` tamamlandığında, bunun <xref:System.Activities.CompletionCallback> sonucu, adında `result`türü kesin belirlenmiş bir parametre ile kullanılabilir hale gelir. Eğer `true`, `MyWhile` öğesini çağırır<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>,öğesinive olarakgeçirerek.`InternalExecute` `Body` <xref:System.Activities.Activity> <xref:System.Activities.CompletionCallback> Yürütmesi `Body` tamamlandığında, `Condition` içinde `InternalExecute`yeniden zamanlanır ve döngü tekrar başlar. `false` `MyWhile` `Body` 'İ<xref:System.Activities.ActivityInstanceState.Closed> döndüğünde, bir örneği, zamanlamayı zamanlamadan çalışma zamanına bir denetim verir ve çalışma zamanı onu duruma getirir. `Condition`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Visual Studio 2010 ' de bileşik. sln örnek çözümünü açın.

2. Çözümü derleyin ve çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
