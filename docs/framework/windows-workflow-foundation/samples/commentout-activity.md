---
title: CommentOut etkinliği
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 3e9f6945755bd60c551674ea8a3471a9f612da52
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404756"
---
# <a name="commentout-activity"></a>CommentOut etkinliği
Bu örnek nasıl etkili bir şekilde bunları yorum yürütmesinin yolundan diğer etkinlikleri kaldıran özel bir etkinlik yazılacağını gösterir.  
  
## <a name="the-commentout-activity"></a>CommentOut etkinliği  
 Kendi hedefe ulaşmak için CommentOut etkinliği türetildiği <xref:System.Activities.CodeActivity> temel sınıfı ve boş bir uygulayan <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.  
  
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
  
 `Designer` Tasarım zamanında etkinliğin görsel arabirimi uygulayan Sınıf özniteliği belirtir. `ContentProperty` Öznitelik bildirir `"Body"` özelliği bu etkinlik bir örneğini XAML gösterimini atlandı.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 Tasarımcı sınıfında, XAML etkinlik özel görsel bir temsilini oluşturmak için kullanılır. <xref:System.Activities.Presentation.WorkflowItemPresenter> görsel Düzenleyici sağlar bir sınıftır.  
  
 Tek bir etkinlik üzerine bırakılabilir `CommentOut` etkinlik yüzeyi. Birden çok etkinlik bu yüzeyine eklemek istiyorsanız, bir sıralama etkinliği Buraya ilk sürükleyin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  İçinde CommentOut.sln açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak Çözümü derleyin.  
  
3.  Örnek, CTRL + F5 tuşlarına basarak hata ayıklama olmadan başlat.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
