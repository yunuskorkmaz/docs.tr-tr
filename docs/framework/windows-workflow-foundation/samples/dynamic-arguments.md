---
title: Dinamik bağımsız değişkenleri
ms.date: 03/30/2017
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
ms.openlocfilehash: dcf6b84889f3bd7d043f736336c39634cd5384c7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387246"
---
# <a name="dynamic-arguments"></a>Dinamik bağımsız değişkenleri
Bu örnek, bağımsız değişkenler etkinlik Yazar yerine etkinlik tüketici tarafından tanımlanan bir etkinlik uygulayan gösterilmiştir. Bunu etkinliğe ilişkin meta veri çalışma zamanı oluşturur yolu geçersiz kılarak yapar.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Yürütme önce çalışma zamanı etkinlik türü genel üyeleri inceleme ve etkinlik meta verilerini bir parçası olarak otomatik olarak bağımsız değişkenler, değişkenleri, alt etkinlikleri ve etkinlik temsilcileri bildirme açıklaması bir etkinlik oluşturur. Çalışma zamanı ilişkilerini ve lifetime kuralları yönetmek için farklı bir iş akışı de doğru yapımı emin olmak için bunu yapar. Öğesinden türetilen etkinlik türü genel üyeler belirterek bir etkinlik Yazar etkinlik bağımsız değişkenleri genellikle tanımlar <xref:System.Activities.Argument>. Öğesinden türetilen her bir ortak üye için <xref:System.Activities.Argument>, çalışma zamanı oluşturur bir <xref:System.Activities.RuntimeArgument> ve kullanıcı tarafından sağlanan bağımsız değişken bu üyede ayarlamak için bağlar. Bazı durumlarda, ancak tüketici etkinliğin bağımsız değişken kümesinin belirleyen bazı yapılandırma sağlar. Bir etkinlik Yazar geçersiz kılmalar <xref:System.Activities.Activity.CacheMetadata%2A> şekilde etkinlik özelleştirmek için meta verileri, etkinliği ile ilişkili bağımsız değişkenler kümesini içeren yerleşik olarak bulunur.  
  
 Bu örnek nasıl dinamik olarak bir yöntemi çağıran bir etkinliğin bağımsız değişken listesi oluşturulacağını gösterir. Etkinlik tüketici türü ve bu yönteme gönderilecek bağımsız değişkenlerin koleksiyonunu birlikte çağrılacak istedikleri yöntem adını belirtir.  
  
> [!NOTE]
>  Bu örnek amacı nasıl geçersiz kılınacağını göstermektir <xref:System.Activities.CodeActivity.CacheMetadata%2A> ve nasıl kullanılacağını <xref:System.Activities.RuntimeArgument>. Bu etkinlik çağırabilirsiniz yöntemler tür göre çeşitli uyarılar vardır. Örneğin, genel türler veya parametre dizileri ile çalışmaz. <xref:System.Activities.Statements.InvokeMethod> Framework derlemelerindeki birlikte gelen etkinlik işleme bu cases ve daha fazlası.  
  
 `MethodInvoke` Etkinliği geçersiz kılmaları <xref:System.Activities.CodeActivity.CacheMetadata%2A> ve oluşturarak başlıyor bir <xref:System.Activities.RuntimeArgument> herhangi yöntemi çağrısının sonucunu işlemek için. Bu bağlar <xref:System.Activities.RuntimeArgument> için herkese açık şekilde ayarlanabilir <xref:System.Activities.OutArgument> adlı `Result`. `MethodInvoke.Result` Olan `null`, çalışma zamanı ile otomatik olarak dolduran bir <xref:System.Activities.OutArgument> kendi türünün varsayılan ifadesiyle yapılandırılmış. Bir etkinlik Yazar hiçbir zaman sahip bir bağımsız değişken özelliği olup olmadığını denetlemek Bu davranış olduğu anlamına gelir `null`.  
  
 Ardından, <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılma belirler `MethodInfo` kullanıcı tarafından sağlanan çağrısından kullanacağı `MethodName` ve `TargetType`. `DetermineMethodInfo` Yöntemi <xref:System.Activities.CodeActivityMetadata> geçirilen <xref:System.Activities.CodeActivity.CacheMetadata%2A> yapılandırma hataları doğrulama hataları bildirilebilir olacak şekilde geçersiz kılın. Bu çağrılarak gerçekleştirilir `metadata.AddValidationError`.  
  
 Bir kez `MethodInfo` , örnek yinelenir üzerinden ayarlanmadı `MethodInfo` parametreleri. Her parametre için oluşturduğu bir <xref:System.Activities.RuntimeArgument> ve kullanıcı tarafından sağlanan koleksiyondan karşılık gelen bağımsız değişken bağlar `Parameters` özelliği. Son olarak, koleksiyonu <xref:System.Activities.RuntimeArgument>s etkinliği ile ilişkili çağırarak `metadata.SetArgumentsCollection`.  
  
 Bağımsız değişken çözümleme yapılabilir Not kullanarak bir <xref:System.Activities.RuntimeArgument>, durumunda gibi `resultArgument` ya da olduğu gibi kullanıcı tarafından sağlanan bağımsız değişken `Parameters` koleksiyonu.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DynamicArguments.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`