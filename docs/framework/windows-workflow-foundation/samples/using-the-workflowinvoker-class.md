---
title: Workflowınvoker sınıfını kullanma
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: d6525dbbd30aae95be4c4ee1de267736e557a541
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552211"
---
# <a name="using-the-workflowinvoker-class"></a>Workflowınvoker sınıfını kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.WorkflowInvoker> bir yöntemi gibi bir etkinlik başlatmak için sınıf.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Kullanarak <xref:System.Activities.WorkflowInvoker> sınıfı, bir etkinlik yürütmek için en basit yolu. Bir yöntem çağrısının değilmiş gibi doğrudan bir aktivite çalıştırmak için tasarlanmıştır. Burada etkinliğin yürütülmesine barındırma diğer Çeşitlemeler tarafından sağlanan denetim altyapı gerektirmez senaryolarında kullanım için basit, yüksek performanslı, kullanımı kolay bir API'si var.  
  
 Örnek, türetilen özel bir etkinlik kullanır <xref:System.Activities.CodeActivity%601>< Int32\> adlı `Add` iki ekleyen <xref:System.Activities.InArgument%601>, `X` ve `Y`ve döndüren bir `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > türetildiği <xref:System.Activities.Activity%601>< T\>, sahip olduğu bir <xref:System.Activities.OutArgument%601> \<T > adlı `Result`.) A `Dictionary` \<dize, Nesne > aracılığıyla çağrılan etkinliğe bağımsız değişkenleri iletmek için kullanılan <xref:System.Activities.WorkflowInvoker>. Sözlük anahtarı çağrılan etkinlik bağımsız değişken adına karşılık gelir. Belirli bir anahtar ile ilişkili değer anahtarla tanımlanan bağımsız değişkene bağlıdır.  
  
 Örnek aramalar <xref:System.Activities.WorkflowInvoker.Invoke%2A> ve değerlerini içeren bir sözlük geçirir `X` ve `Y`. <xref:System.Activities.WorkflowInvoker> Sınıfı bu değerleri bağlar `Add` etkinlik bağımsız değişkenlerin bir etkinliği yürütür ve sonucu döndürür.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Invoker.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`