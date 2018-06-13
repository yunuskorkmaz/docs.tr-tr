---
title: Özel bileşik yerel etkinliğini kullanma
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 78d00a13bdc018946fa20635a47677b1508c1ed1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519216"
---
# <a name="custom-composite-using-native-activity"></a>Özel bileşik yerel etkinliğini kullanma
Bu örnek nasıl yazılacağını göstermektedir bir <xref:System.Activities.NativeActivity> diğer zamanlar <xref:System.Activities.Activity> bir iş akışının yürütme akışını denetlemek için nesneleri. Bu örnek iki ortak denetim akışı, kullandığı sıra ve çalışırken, bunun nasıl yapılacağını göstermek için.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 İle başlayarak `MySequence`, öğesinden türetilen fark edilecek ilk şey. <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> olan <xref:System.Activities.Activity> iş akışı çalışma zamanı tüm tekliflerden gösteren nesne <xref:System.Activities.NativeActivityContext> geçirilen `Execute` yöntemi.  
  
 `MySequence` ortak bir topluluğu gösterir <xref:System.Activities.Activity> iş akışı yazarı tarafından doldurulmuş nesneleri. İş akışı yürütülmeden önce iş akışı çalışma zamanı çağırır <xref:System.Activities.Activity.CacheMetadata%2A> bir iş akışındaki her etkinlik üzerinde yöntemi. Bu işlem sırasında çalışma zamanı verileri kapsamı ve ömür boyu yönetimi için üst-alt ilişki kurar. Varsayılan uygulaması <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi kullanan <xref:System.ComponentModel.TypeDescriptor> örneği için sınıf `MySequence` herhangi bir ortak özellik türü eklemek için etkinlik <xref:System.Activities.Activity> veya <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> alt öğeleri olarak `MySequence` etkinlik.  
  
 Aktivite ortak bir alt etkinlikler koleksiyonu gösterir olduğunda, bu alt etkinliklerin durumunu paylaşan olasıdır. Üst etkinlik için en iyi uygulama bu durumda olan `MySequence`, ayrıca bir koleksiyon üzerinden alt etkinlikleri gerçekleştirmek bu değişkenlerin kullanıma sunmak için. Alt etkinlikler gibi <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi ekler türünün ortak özelliklerine <xref:System.Activities.Variable> veya <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> ile ilişkili değişkenleri olarak `MySequence` etkinlik.  
  
 Genel değişkenler yanı sıra hangi yönetilen alt tarafından `MySequence`, `MySequence` aynı zamanda, alt öğelerinin yürütmede olduğu izlenmesi gerekir. Özel bir değişkene kullanan `currentIndex`, bunu başarmak için. Bu değişken bir parçası olarak kayıtlı `MySequence` yapılan bir çağrı ekleyerek ortamı <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> yöntemi içinde `MySequence` etkinliğin <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi. <xref:System.Activities.Activity> Eklenen nesneleri `MySequence` `Activities` koleksiyon değişkenleri bu şekilde eklenen erişemiyor.  
  
 Zaman `MySequence` çalışma zamanı tarafından çalışma zamanı çağrıları yürütülen kendi <xref:System.Activities.NativeActivity.Execute%2A> tümleştirilmesidir yöntemi, bir <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> Etkinliğin proxy bağımsız değişkenleri ve değişkenleri başvurusunun kaldırılmasının yanı sıra diğer zamanlama için yeniden çalışma zamanı içine <xref:System.Activities.Activity> nesneleri veya `ActivityDelegates`. `MySequence` kullanan bir `InternalExecute` ilk alt ve tek bir yöntem sonraki tüm alt öğeleri zamanlama mantığını saklamak üzere yöntemi. Başvurusunun kaldırılmasının tarafından başlatır `currentIndex`. Sayıma eşit ise `Activities` koleksiyonu sonra sırası tamamlandığında, etkinlik herhangi bir iş zamanlaması olmadan döndürür ve çalışma zamanı içine taşır <xref:System.Activities.ActivityInstanceState.Closed> durumu. Varsa `currentIndex` küçük etkinlikleri sayısından sonraki alt alanından elde edilen `Activities` koleksiyonu ve `MySequence` çağrıları <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, alt zamanlanması için geçen ve <xref:System.Activities.CompletionCallback> işaret adresindeki `InternalExecute` yöntem. Son olarak, `currentIndex` artırılır ve denetim çalışma zamanına belirlenmiştir. En çok bir örneği olarak `MySequence` alt sahip <xref:System.Activities.Activity> zamanlanmış nesnesi, çalışma zamanı göz önünde bulundurur yürütülme durumunda olması için.  
  
 Alt etkinlik tamamlandığında <xref:System.Activities.CompletionCallback> yürütülür. Döngü üstten devam eder. Gibi `Execute`, <xref:System.Activities.CompletionCallback> geçen bir <xref:System.Activities.NativeActivityContext>, çalışma zamanı uygulayan erişim veren.  
  
 `MyWhile` farklı `MySequence` tek bir zamanlar, <xref:System.Activities.Activity> art arda nesne ve kullanan bir <xref:System.Activities.Activity%601>< bool\> adlı `Condition` Bu zamanlama gerçekleşip gerçekleşmediğini belirlemek için. Gibi `MySequence`, `MyWhile` kullanan bir `InternalExecute` yöntemi, zamanlama mantığını merkezileştirme. Bu zamanlamaları `Condition` <xref:System.Activities.Activity>< bool\> ile bir <xref:System.Activities.CompletionCallback%601> \<bool > adlı `OnEvaluationCompleted`. Zaman yürütülmesi `Condition` olan tamamlandı, sonuç bu kullanılabilir duruma <xref:System.Activities.CompletionCallback> adlı kesin türü belirtilmiş bir parametreye `result`. Varsa `true`, `MyWhile` çağrıları <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, içinde geçen `Body` <xref:System.Activities.Activity> nesne ve `InternalExecute` olarak <xref:System.Activities.CompletionCallback>. Zaman yürütülmesi `Body` tamamlandıktan `Condition` yeniden zamanlanmış `InternalExecute`, döngü üzerinden yeniden başlatılıyor. Zaman `Condition` döndürür `false`, örneği `MyWhile` verir denetim geri çalışma zamanına zamanlama olmadan `Body` ve çalışma zamanı taşınır <xref:System.Activities.ActivityInstanceState.Closed> durumu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Composite.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`