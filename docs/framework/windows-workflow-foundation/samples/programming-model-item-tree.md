---
title: Programlama modeli öğesi ağacı
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 497aa75214bdbbefa7f09ef56fe96926c2461ed6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="9cff3-102">Programlama modeli öğesi ağacı</span><span class="sxs-lookup"><span data-stu-id="9cff3-102">Programming Model Item Tree</span></span>
<span data-ttu-id="9cff3-103">Bu örnek gitmek gösterilmiştir <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veri bağlama işlemini kullanma ağacı.</span><span class="sxs-lookup"><span data-stu-id="9cff3-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9cff3-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9cff3-104">Sample Details</span></span>  
 <span data-ttu-id="9cff3-105"><xref:System.Activities.Presentation.Model.ModelItem> Ağacıdır tarafından kullanılan soyutlama [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] düzenlenmekte olan temeldeki örnek hakkındaki verileri kullanıma sunmak için altyapı.</span><span class="sxs-lookup"><span data-stu-id="9cff3-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="9cff3-106">Aşağıdaki çizimde altyapısı içinde çeşitli katmanlarına bir gösterimi olan [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cff3-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>  
  
 <span data-ttu-id="9cff3-107">![İş Akışı Tasarımcısı mimarisi](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span><span class="sxs-lookup"><span data-stu-id="9cff3-107">![Workflow Designer Architecture](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span></span>  
  
 <span data-ttu-id="9cff3-108">A <xref:System.Activities.Presentation.Model.ModelItem> koleksiyonu yanı sıra temel alınan değer için bir işaretçi oluşan <xref:System.Activities.Presentation.Model.ModelProperty> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9cff3-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="9cff3-109">A <xref:System.Activities.Presentation.Model.ModelProperty> nesnesi sırayla oluşur adı ve türü özelliği ve buna karşılık, başka değeri için bir işaretçi gibi veri <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="9cff3-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="9cff3-110">Değer Dönüştürücüsü Bazı işlemek için kullanılan <xref:System.Activities.Presentation.Model.ModelItem>döndürülen s bir <xref:System.Activities.Presentation.Model.ModelProperty> bunları doğru ağaç görünümünde görünür hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="9cff3-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="9cff3-111">Örnek sonra imperatively karşı programlamayı gösteren <xref:System.Activities.Presentation.Model.ModelItem> kesinlik temelli söz dizimini kullanarak aşağıdaki örnekte görüldüğü gibi ağacı.</span><span class="sxs-lookup"><span data-stu-id="9cff3-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9cff3-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9cff3-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="9cff3-113">ProgrammingModelItemTree.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cff3-113">Open the ProgrammingModelItemTree.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9cff3-114">Seçerek çözümü derleme **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9cff3-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="9cff3-115">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9cff3-115">Press F5 to run the application.</span></span> <span data-ttu-id="9cff3-116">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Form sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9cff3-116">The [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] form is then displayed.</span></span>  
  
4.  <span data-ttu-id="9cff3-117">Tıklatın **yük WF** yüklemek için düğmeyi <xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlayın.</span><span class="sxs-lookup"><span data-stu-id="9cff3-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>  
  
5.  <span data-ttu-id="9cff3-118">Tıklatarak **değişiklik Model öğesi ağacı** düğmesi ağacına bir öğe ekleyin ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="9cff3-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9cff3-119">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="9cff3-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9cff3-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9cff3-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9cff3-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9cff3-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9cff3-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9cff3-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="9cff3-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9cff3-123">See Also</span></span>  
 <xref:System.Windows.Data.IValueConverter>
