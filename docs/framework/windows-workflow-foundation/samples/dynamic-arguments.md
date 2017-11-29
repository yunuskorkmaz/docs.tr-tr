---
title: "Dinamik değişkenleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 212f2df9e84a4af4e1c9e7d6792277adfb17351d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-arguments"></a>Dinamik değişkenleri
Bu örnek, bağımsız değişkenler etkinlik Yazar yerine etkinlik tüketici tarafından tanımlanan bir etkinlik uygulayan gösterilmiştir. Çalışma zamanı etkinliğe ilişkin meta veri yapılarını yolu geçersiz kılarak bunu yapar.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Yürütme önce çalışma zamanı etkinlik türü ortak üyelerine incelenerek ve bağımsız değişkenler, değişkenleri, alt etkinlikleri ve etkinlik temsilciler bir etkinliğin meta verilerinin bir parçası otomatik olarak bildirme tarafından bir etkinlik açıklamasını oluşturur. Çalışma zamanı ilişkileri ve yaşam süresi kurallarını yönetmek için bir iş akışı da doğru yapımı emin olmak için bunu yapar. Öğesinden türetilen etkinlik türü üzerinde Genel üyeler belirterek bir etkinlik Yazar etkinliğin bağımsız değişkenler genellikle tanımlar <xref:System.Activities.Argument>. Türetilen ortak her üye için <xref:System.Activities.Argument>, çalışma zamanı oluşturur bir <xref:System.Activities.RuntimeArgument> ve bu üyede ayarlamak kullanıcı tarafından sağlanan bağımsız değişken bağlar. Bazı durumlarda, ancak, bağımsız değişkenler kümesine belirler bazı yapılandırma etkinliğin tüketici sağlar. Bir etkinlik Yazar geçersiz kılmaları <xref:System.Activities.Activity.CacheMetadata%2A> şekilde etkinlik özelleştirmek için meta verileri, etkinliği ile ilişkili bağımsız değişkenler kümesine içeren yerleşik olarak bulunur.  
  
 Bu örnek bir bağımsız değişken listesi dinamik olarak yöntemini çağıran bir etkinliğin nasıl oluşturulacağını gösterir. Etkinlik tüketici türü ve bu yönteme geçirilecek bağımsız değişkenler koleksiyonu birlikte çağrılacak istedikleri yöntem adını belirtir.  
  
> [!NOTE]
>  Bu örnek amacı nasıl geçersiz kılınacağı göstermektir <xref:System.Activities.CodeActivity.CacheMetadata%2A> ve nasıl kullanılacağını <xref:System.Activities.RuntimeArgument>. Bu etkinlik çağırabileceği yöntemleri türlerini göre çeşitli uyarılar vardır. Örneğin, genel türler veya parametre dizileri ile çalışmaz. <xref:System.Activities.Statements.InvokeMethod> İn.NET Framework birlikte gelen etkinlik bu durumlar ve daha fazlasını işler.  
  
 `MethodInvoke` Etkinliği geçersiz kılmaları <xref:System.Activities.CodeActivity.CacheMetadata%2A> ve oluşturarak başlar bir <xref:System.Activities.RuntimeArgument> yöntemi çağırma herhangi sonucundan işlemek için. Bu bağlar <xref:System.Activities.RuntimeArgument> herkese açık şekilde ayarlanabilir için <xref:System.Activities.OutArgument> adlı `Result`. Varsa `MethodInvoke.Result` olan `null`, çalışma zamanı ile otomatik olarak doldurur bir <xref:System.Activities.OutArgument> kendi türü için varsayılan ifadesi ile yapılandırılır. Bir etkinlik Yazar hiçbir zaman sahip bir bağımsız değişken özelliği olup olmadığını denetlemek Bu davranış anlamına gelir `null`.  
  
 Ardından, <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılma belirler `MethodInfo` kullanıcı tarafından sağlanan çağrısından kullanacağı `MethodName` ve `TargetType`. `DetermineMethodInfo` Yöntemi alır <xref:System.Activities.CodeActivityMetadata> parametresi geçirilen <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hataları bildirilebilir. yapılandırma hataları böylece geçersiz kıl. Bu çağırarak yapılır `metadata.AddValidationError`.  
  
 Bir kez `MethodInfo` , örnek tekrarlanan üzerinden ayarlanmadı `MethodInfo` parametreleri. Her bir parametreyi oluşturduğu bir <xref:System.Activities.RuntimeArgument> ve kullanıcı tarafından sağlanan koleksiyondan karşılık gelen değişkeninde bağlandığı `Parameters` özelliği. Son olarak, koleksiyonunu <xref:System.Activities.RuntimeArgument>s etkinliği ile ilişkili çağırarak `metadata.SetArgumentsCollection`.  
  
 Bağımsız değişken çözümleme yapılabilir Not kullanarak bir <xref:System.Activities.RuntimeArgument>, durumunda gibi `resultArgument` veya durumunda olduğu gibi kullanıcı tarafından sağlanan bağımsız değişken `Parameters` koleksiyonu.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DynamicArguments.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`  
  
## <a name="see-also"></a>Ayrıca Bkz.
