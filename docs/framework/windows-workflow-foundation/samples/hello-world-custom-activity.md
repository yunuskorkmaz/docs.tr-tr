---
title: Merhaba Dünya özel etkinliği
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470781"
---
# <a name="hello-world-custom-activity"></a>Merhaba Dünya özel etkinliği
Bu örnek, Windows Workflow Foundation (basit bir özel etkinlik oluşturma da dahil olmak üzere WF), birkaç temel özellikleri gösterir. Bu örnekte gösterilen özelliklerin bazıları C# ve kullanarak özel bir etkinlik oluşturmakta olduğunuz `in` ve `out` bağımsız değişkenleri (<xref:System.Activities.InArgument> ve <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Kodda bir iş akışı oluşturma  
 Bu örnekte, iki özel etkinlikler, C# kodunu kullanarak oluşturulur. Her iki özel etkinlikler doğrudan veya dolaylı olarak devralınacak <xref:System.Activities.Activity%601> tek bir değer. Genel olmayan devralan yerine genel dönüş değeri kullanmanın avantajı <xref:System.Activities.Activity> sınıfı, bazı etkinlikler olan (gibi <xref:System.Activities.Statements.Assign>) oluşan bir etkinlik bir parçası olarak kullanıldığında döndürülen değer erişebilir.  
  
 AppendString  
 Bu etkinlik devraldığı <xref:System.Activities.Activity%601>ve kullandığı bir <xref:System.Activities.Statements.Assign> birlikte iki dizeyi art arda ekler etkinlik.  
  
 Dize önüne ekleyin  
 Bu etkinlik, doğrudan devralan <xref:System.Activities.CodeActivity%601>ve benzer bir işlevsellik oluşturur `AppendString` etkinliği kod yerine önceden varolan bir etkinliğin oluşturuluyor uygulanan mantığı kullanır.  
  
 Aşağıdaki dosyalar bu projeye eklenir.  
  
 AppendString.cs  
 Özel Etkinlik dizeleri birlikte ekler. Bu, bir dize alır ve "Merhaba Dünya forma çıktı olarak tam bir ileti yazan" sabit metin dizesi ile birleştirir.  
  
 PrependString.cs  
 Bu etkinliğin bir Giriş dizesinin için önceden tanımlanmış bir dize ekler.  
  
 Sequence1.xaml  
 Kullanan bir iş akışı `AppendString` ve `PrependString` özel etkinlikler.  
  
 Program.cs  
 İş akışının çalıştığı bir programdır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], HelloWorld.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.