---
title: "CommentOut etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: df5faa2aacf6b86d708dad4b157b27d2609a0a93
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="commentout-activity"></a>CommentOut etkinliği
Bu örnek, yolun etkili bir şekilde bunları yorum yürütülmesinin diğer etkinlikler kaldırır özel bir etkinlik yazma gösterilmiştir.  
  
## <a name="the-commentout-activity"></a>CommentOut etkinliği  
 Kendi hedefe ulaşmak için CommentOut etkinlik türeyen <xref:System.Activities.CodeActivity> temel sınıfı ve boş bir uygulayan <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 Sınıfı, aşağıdaki örnekte gösterildiği gibi bildirilir.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` Özniteliği tasarım zamanında etkinliğin visual arabirimini uygulayan sınıfı belirtir. `ContentProperty` Öznitelik bildirir `"Body"` özelliği bu etkinliği örneği XAML gösterimini atlandı.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 Tasarımcı sınıfında XAML özel görsel bir etkinlik oluşturmak için kullanılır. <xref:System.Activities.Presentation.WorkflowItemPresenter>görsel Düzenleyici sunar bir sınıftır.  
  
 Tek bir etkinliğin üzerine bırakılabilir `CommentOut` etkinlik yüzeyini. Bu yüzeye birden çok etkinliği eklemek istiyorsanız, bir dizi etkinlik Buraya ilk sürükleyin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  İçinde CommentOut.sln açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşuna basarak Çözümü derleyin.  
  
3.  Örnek, CTRL + F5'e basarak hata ayıklama olmadan başlat.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
