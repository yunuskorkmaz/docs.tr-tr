---
title: InvokeMethod etkinliğini kullanma
ms.date: 03/30/2017
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
ms.openlocfilehash: f6e32d002a4a2002037a6d74c5a2c3e275568efb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-invokemethod-activity"></a>InvokeMethod etkinliğini kullanma
Bu örnek nasıl kullanılacağı ortaya <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) ortak sınıflarda ortak yöntemleri çağırmak için etkinlik. <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Etkinlik nesneleri karşı yöntemlerini çağırın, parametreleri geçirin, dönüş değeri almak, genel yöntemler için türlerini belirtme ve yöntemi zaman uyumlu olup olmadığını belirlemek için iş akışı izin verir veya zaman uyumsuz. 
  
Genel olmayan sürümü <xref:System.Activities.Statements.InvokeMethod> için dönüş değerini ayarlandığı etkinlik <xref:System.Activities.Statements.InvokeMethod.Result%2A> özelliği ve genel bir sürümü <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) etkinlik burada dönüş değeri döndürülür aracılığıyla <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) türündeki özelliği `TResult`. 
  
 Bu örnek, çeşitli yöntemi türleri çağırmayı gösterir. Aşağıdaki liste ayrıntıları yöntemi türleri bu örnekte gösterilmiştir:  
  
-   Parametresiz bir örnek yöntemi çağırır.  
  
-   Örnek yöntemi iki parametre (System.String ve System.Int32) ile çağırır.  
  
-   Örnek yöntemi iki parametre (System.String ve System.Int32) ve System.String [] türünde bir parametre dizisi ile çağırır.  
  
-   Örnek yöntemi iki parametre (iki System.Int32 sayılar) ile ve bir sonuç türü System.Int32 çağırır.  
  
     Dönüş değeri bir değişkene bağlı ve konsolunu kullanarak yazdırılan <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
-   İki parametre (System.String ve System.Int32) ile statik bir yöntemi çağırır.  
  
-   Bir genel parametre (System.String) ile örnek yöntemi çağırır.  
  
-   İki genel parametreleri (System.String ve System.Int32) olan bir statik yöntem çağırır.  
  
-   Başvuru (System.String) tarafından geçirilen bir parametre olan örnek yöntemi çağırır.  
  
     Başvurulan parametresi bir değişkene bağlı ve konsolunu kullanarak yazdırılan <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
-   Zaman uyumsuz örnek yöntemi çağırır.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], InvokeMethodUsage.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`