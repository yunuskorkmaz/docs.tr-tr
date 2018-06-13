---
title: CommentOut etkinliği
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 7847f4e1d77c2927a27be6b83f4016a22e4e3b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515202"
---
# <a name="commentout-activity"></a><span data-ttu-id="05d4a-102">CommentOut etkinliği</span><span class="sxs-lookup"><span data-stu-id="05d4a-102">CommentOut Activity</span></span>
<span data-ttu-id="05d4a-103">Bu örnek, yolun etkili bir şekilde bunları yorum yürütülmesinin diğer etkinlikler kaldırır özel bir etkinlik yazma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05d4a-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="05d4a-104">CommentOut etkinliği</span><span class="sxs-lookup"><span data-stu-id="05d4a-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="05d4a-105">Kendi hedefe ulaşmak için CommentOut etkinlik türeyen <xref:System.Activities.CodeActivity> temel sınıfı ve boş bir uygulayan <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05d4a-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="05d4a-106">Sınıfı, aşağıdaki örnekte gösterildiği gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="05d4a-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="05d4a-107">`Designer` Özniteliği tasarım zamanında etkinliğin visual arabirimini uygulayan sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="05d4a-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="05d4a-108">`ContentProperty` Öznitelik bildirir `"Body"` özelliği bu etkinliği örneği XAML gösterimini atlandı.</span><span class="sxs-lookup"><span data-stu-id="05d4a-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="05d4a-109">Tasarımcı sınıfında XAML özel görsel bir etkinlik oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05d4a-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="05d4a-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> görsel Düzenleyici sunar bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="05d4a-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="05d4a-111">Tek bir etkinliğin üzerine bırakılabilir `CommentOut` etkinlik yüzeyini.</span><span class="sxs-lookup"><span data-stu-id="05d4a-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="05d4a-112">Bu yüzeye birden çok etkinliği eklemek istiyorsanız, bir dizi etkinlik Buraya ilk sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="05d4a-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="05d4a-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="05d4a-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="05d4a-114">İçinde CommentOut.sln açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05d4a-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="05d4a-115">CTRL + SHIFT + B tuşuna basarak Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="05d4a-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="05d4a-116">Örnek, CTRL + F5'e basarak hata ayıklama olmadan başlat.</span><span class="sxs-lookup"><span data-stu-id="05d4a-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05d4a-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="05d4a-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="05d4a-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="05d4a-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05d4a-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="05d4a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05d4a-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="05d4a-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
