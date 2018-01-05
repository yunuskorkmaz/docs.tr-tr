---
title: "WorkflowInvoker sınıfını kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 553367916ff249118a8fcdd8273382402b90cfcc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-workflowinvoker-class"></a>WorkflowInvoker sınıfını kullanma
Bu örnek nasıl kullanılacağı ortaya <xref:System.Activities.WorkflowInvoker> bir yöntem değilmiş gibi bir etkinlik çağrılacak sınıfı.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Kullanarak <xref:System.Activities.WorkflowInvoker> bir aktivite çalıştırmak için en basit yolu bir sınıftır. Yöntem çağrısı değilmiş gibi doğrudan bir aktivite çalıştırmak için tasarlanmıştır. Burada bir etkinliğin yürütme barındırma diğer Çeşitleme tarafından sağlanan denetim altyapı gerektirmez senaryolarda kullanım için basit, yüksek performanslı, kullanımı kolay bir API değil.  
  
 Örnek türetilen özel bir aktivite kullanır <xref:System.Activities.CodeActivity%601>< Int32\> adlı `Add` iki ekleyen <xref:System.Activities.InArgument%601>, `X` ve `Y`ve döndüren bir `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > türetilen <xref:System.Activities.Activity%601>< T\>, sahip olduğu bir <xref:System.Activities.OutArgument%601> \<T > adlı `Result`.) A `Dictionary` \<dize, Nesne > bağımsız değişkenleri aracılığıyla çağrılan etkinliğe geçirmek için kullanılan <xref:System.Activities.WorkflowInvoker>. Anahtarı sözlük çağrılan etkinlik bağımsız değişken adını karşılık gelir. Belirli bir anahtarla ilişkilendirilen değeri anahtarı tarafından tanımlanan bağımsız değişkeni bağlıdır.  
  
 Örnek aramalar <xref:System.Activities.WorkflowInvoker.Invoke%2A> ve değerlerini içeren bir sözlük geçirir `X` ve `Y`. <xref:System.Activities.WorkflowInvoker> Sınıfı bu değerleri bağlar `Add` etkinlik bağımsız değişkenlerini kullanıcının, etkinlik yürütür ve sonucu döndürür.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Invoker.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`