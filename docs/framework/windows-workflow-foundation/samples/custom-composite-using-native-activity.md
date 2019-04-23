---
title: Native Etkinliği Kullanan Özel Bileşik
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 41a823ab00a2be0772a07b15d1292dbb4e8d1a6b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340301"
---
# <a name="custom-composite-using-native-activity"></a>Native Etkinliği Kullanan Özel Bileşik
Bu örnek nasıl yazılacağını gösterir. bir <xref:System.Activities.NativeActivity> diğer zamanlayan <xref:System.Activities.Activity> nesneleri, bir iş akışının yürütmenin akışını denetlemek için. Bu örnek iki ortak denetim akışı kullanan sıra ve çalışırken, bunun nasıl yapılacağını göstermek için.

## <a name="sample-details"></a>Örnek Ayrıntıları
 İle başlayarak `MySequence`, fark edilecek ilk şey öğesinden türetilen olan <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> olan <xref:System.Activities.Activity> teknolojilerimizden iş akışı çalışma zamanı kullanıma sunduğu nesne <xref:System.Activities.NativeActivityContext> geçirilen `Execute` yöntemi.

 `MySequence` Genel koleksiyonu sunan <xref:System.Activities.Activity> nesneler iş akışı yazar tarafından doldurulur. İş akışı yürütülmeden önce iş akışı çalışma zamanı çağırır <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi bir iş akışındaki her etkinlik. Bu işlem sırasında çalışma zamanı veri kapsamı ve ömür yönetimi için üst-alt ilişkilerini belirler. Varsayılan uygulaması <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi kullanan <xref:System.ComponentModel.TypeDescriptor> örnek sınıfı için `MySequence` herhangi bir ortak özellik türü eklemek için etkinlik <xref:System.Activities.Activity> veya <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> alt olarak `MySequence` etkinlik.

 Bir etkinlik, çocuk etkinliklerinin genel koleksiyonu sunar olduğunda, bu çocuk etkinliklerinin durum paylaşma olasıdır. Bu durumda en iyi uygulama ana etkinlik için olan `MySequence`, ayrıca, çocuk etkinliklerinin gerçekleştirmek bu değişkeni koleksiyonunu kullanıma sunmak için. Bağımlı etkinlikler, ister <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi ekler türünün ortak özelliklerine <xref:System.Activities.Variable> veya <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> değişkenleri ile ilişkili olarak `MySequence` etkinlik.

 Genel değişkenleri yanı sıra, yönetilen alt tarafından `MySequence`, `MySequence` alt yürütme olduğu, izleme tutmalıdır. Özel bir değişken kullanan `currentIndex`, bunu gerçekleştirmek için. Bu değişken bir parçası olarak kayıtlı `MySequence` çağrısı ekleyerek ortamı <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> yöntemi içinde `MySequence` etkinliğin <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi. <xref:System.Activities.Activity> Eklenen nesneleri `MySequence` `Activities` koleksiyon değişkenleri böylece eklenen erişemez.

 Zaman `MySequence` çalışma zamanında, çalışma zamanı çağrıları yürütülür, <xref:System.Activities.NativeActivity.Execute%2A> tümleştirilmesidir yöntemi, bir <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> Etkinliğin proxy bağımsız değişkenleri ve değişkenleri başvuruluyor yanı sıra diğer zamanlama için yeniden çalışma zamanı içinde <xref:System.Activities.Activity> nesneleri veya `ActivityDelegates`. `MySequence` kullanan bir `InternalExecute` ilk alt ve tek bir yöntem sonraki tüm alt öğeleri zamanlama mantığı kapsülleyen yöntemi. Tarafından başvuruluyor başladıktan `currentIndex`. Sayı eşit olup olmadığını `Activities` koleksiyonu ve ardından sırası tamamlandığında, etkinlik herhangi bir iş zamanlama olmadan döndürür ve çalışma zamanı içine taşır <xref:System.Activities.ActivityInstanceState.Closed> durumu. Varsa `currentIndex` küçük etkinlikleri sayısından öğesinden sonraki alt alınır `Activities` koleksiyonu ve `MySequence` çağrıları <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, zamanlanmış alt geçen ve <xref:System.Activities.CompletionCallback> sırasında işaret eden `InternalExecute` yöntem. Son olarak, `currentIndex` artırılır ve yeniden çalışma zamanı denetimi üretilenleri kaydeder. Olduğu sürece bir örneğini `MySequence` bir çocuğu <xref:System.Activities.Activity> zamanlanmış nesnesi, çalışma zamanı dikkate yürütülme durumunda olmasını.

 Alt etkinlik tamamlandığında <xref:System.Activities.CompletionCallback> yürütülür. Döngü En üstten devam eder. Gibi `Execute`, <xref:System.Activities.CompletionCallback> alır bir <xref:System.Activities.NativeActivityContext>, çalışma zamanına uygulayan erişim sağlar.

 `MyWhile` farklıdır `MySequence` içeren tek bir zamanlar <xref:System.Activities.Activity> sürekli olarak nesne ve kullanan bir <xref:System.Activities.Activity%601>< bool\> adlı `Condition` Bu zamanlama gerçekleşip gerçekleşmediğini belirleme. Gibi `MySequence`, `MyWhile` kullanan bir `InternalExecute` zamanlama mantığını merkezileştirmek için yöntemi. Bu zamanlamaları `Condition` <xref:System.Activities.Activity>< bool\> ile bir <xref:System.Activities.CompletionCallback%601> \<bool > adlı `OnEvaluationCompleted`. Zaman yürütülmesini `Condition` olan tamamlandı, sonuç bu kullanılabilir duruma <xref:System.Activities.CompletionCallback> adlı kesin türü belirtilmiş bir parametre içinde `result`. Varsa `true`, `MyWhile` çağrıları <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, içinde geçen `Body` <xref:System.Activities.Activity> nesne ve `InternalExecute` olarak <xref:System.Activities.CompletionCallback>. Zaman yürütülmesini `Body` tamamlanır `Condition` yeniden zamanlanmış `InternalExecute`, döngü yeniden başlatılıyor. Zaman `Condition` döndürür `false`, örneği `MyWhile` verir denetimi yeniden çalışma zamanı zamanlama olmadan `Body` ve çalışma zamanı taşır <xref:System.Activities.ActivityInstanceState.Closed> durumu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Composite.sln örnek çözüm, Visual Studio 2010'da açın.

2. Derleme ve çözümü çalıştırın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`