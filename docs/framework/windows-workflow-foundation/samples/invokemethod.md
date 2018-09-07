---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047717"
---
# <a name="invokemethod"></a>InvokeMethod
Bu örnek, kullanarak farklı yollarını gösterir. <xref:System.Activities.Statements.InvokeMethod> sınıfının yöntemlerini çağırmak için etkinlik.  
  
 Bir yöntem, bir sınıfa aittir ve kapsanan bir işlemler kümesini temsil eder. <xref:System.Activities.Statements.InvokeMethod> Etkinlik nesneleri veya türlerine karşı yöntemleri çağırmak, parametreleri geçirin ve dönüş değeri elde etmek için yeteneği sağlar. Yöntemler, zaman uyumlu veya zaman uyumsuz olarak çağrılabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte <xref:System.Activities.Statements.InvokeMethod> etkinlik aşağıdaki senaryoları gerçekleştirmek için:  
  
1.  Parametresiz örnek yöntemi çağırın.  
  
2.  İki parametre ile bir örnek yöntemi çağırma (<xref:System.String> ve <xref:System.Int32>).  
  
3.  İki parametre ile bir örnek yöntemi çağırma (<xref:System.String> ve <xref:System.Int32>) ve türünde bir parametre dizisi <xref:System.String>[].  
  
4.  Türünde iki parametre ile bir örnek yöntemi Çağır <xref:System.Int32> ve bir sonuç türü <xref:System.Int32>. Bu senaryoda, sonuç değeri bir değişkene bağımlı ve başka bir etkinlikte kullanılır. Konsolunu kullanarak görüntülenir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
5.  Türünde iki parametre ile statik bir yöntemi çağırmak <xref:System.String> ve <xref:System.Int32>.  
  
6.  Bir genel tür parametresi ile bir örnek yöntemi Çağır <xref:System.String>.  
  
7.  İki genel tür parametreleri ile statik bir yöntemi çağırmak <xref:System.String> ve <xref:System.Int32>.  
  
8.  Bir parametre türü bir başvuru tarafından geçirilmediğine sahip bir örnek yöntemi Çağır <xref:System.String>. Bu senaryoda, başvuru parametresi bir değişkene bağlıdır (`outParam`) ve başka bir etkinlikte kullanılır. Konsolunu kullanarak görüntülenir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
9. Bir zaman uyumsuz örnek yöntemini çağırır.  
  
10. Kullanarak iki nesnenin aynı örneğinde iki farklı yöntem çağırma <xref:System.Activities.Statements.InvokeMethod> etkinlikler.  
  
11. Değer bir nesne örneğini Store.  
  
12. Bir nesnenin bir örneğinden bir değer alır.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
 Bu örnek, iki sürümde sağlanır. İlk sürümü bu örnek kullanımını gösterir <xref:System.Activities.Statements.InvokeMethod> C# ile kodlayın Windows Workflow Foundation (WF) programlama modelini kullanarak ve CodedWorkflow\CS klasörü altında bulunabilir. Dosyanın ikinci sürümü kullanımını gösteren <xref:System.Activities.Statements.InvokeMethod> XAML kullanarak ve DesignerWorkflow\CS klasörü altında bulunabilir.  
  
#### <a name="to-run-the-coded-workflow-sample"></a>Kodlanmış bir iş akışı örneği çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CodedWorkflow\CS klasöründe InvokeMethodUsage.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
#### <a name="to-run-the-designer-workflow-sample"></a>Tasarımcı iş akışı örneği çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DesignerWorkflow\CS klasöründe InvokeMethodUsage.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`