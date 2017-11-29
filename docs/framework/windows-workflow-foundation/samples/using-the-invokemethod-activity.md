---
title: "InvokeMethod etkinliğini kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5dd488a01e00af0661ee7ee110c79d2c56a0b777
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## <a name="see-also"></a>Ayrıca Bkz.
