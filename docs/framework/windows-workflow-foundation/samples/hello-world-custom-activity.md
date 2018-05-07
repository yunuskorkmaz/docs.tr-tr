---
title: Hello World özel etkinlik
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: 35ae5933515b3280b0d8d95157c8dd5f40f7b320
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hello-world-custom-activity"></a>Hello World özel etkinlik
Birkaç temel özellikleri, Windows Workflow Foundation (basit bir özel etkinlik oluşturmak nasıl dahil olmak üzere WF), bu örnek gösterilmektedir. Bu örnekte gösterilen özelliklerden bazıları C# ve kullanarak özel bir aktivite oluşturmakta olduğunuz `in` ve `out` bağımsız değişkenler (<xref:System.Activities.InArgument> ve <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Kodda bir iş akışı oluşturma  
 Bu örnekte, iki özel etkinlikler, C# kod kullanılarak oluşturulur. Her iki özel etkinlikler doğrudan veya dolaylı olarak devralınmalıdır <xref:System.Activities.Activity%601> tek bir değer döndürmek için. Genel olmayan devralan yerine genel dönüş değeri kullanmanın avantajı <xref:System.Activities.Activity> sınıfı, bazı etkinlikler olan (gibi <xref:System.Activities.Statements.Assign>) oluşan bir etkinlik bir parçası olarak kullanıldığında dönüş değeri erişebilirsiniz.  
  
 AppendString  
 Bu etkinlik devraldığı <xref:System.Activities.Activity%601>ve kullandığı bir <xref:System.Activities.Statements.Assign> birlikte iki dizeyi art arda ekler etkinlik.  
  
 Dize önüne ekleyin  
 Bu etkinlik doğrudan devraldığı <xref:System.Activities.CodeActivity%601>ve benzer işlevsellik oluşturur `AppendString` kodu yerine önceden var olan bir etkinliğin oluşturuluyor uygulanan mantığını kullanır etkinlik.  
  
 Aşağıdaki dosyaları, bu projede dahil edilir.  
  
 AppendString.cs  
 Dizeleri birlikte ekler Özel Etkinlik. Bir dize alır ve "Merhaba Dünya form çıktı olarak tam bir ileti söyler" bir metin dizesiyle birleştirir.  
  
 PrependString.cs  
 Bu etkinliğin bir giriş dizesi için önceden tanımlanmış bir dize ekler.  
  
 Sequence1.xaml  
 Kullanan bir iş akışı `AppendString` ve `PrependString` özel etkinlikler.  
  
 Program.cs  
 İş akışı tarafından çalıştırılan bir program.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], HelloWorld.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.