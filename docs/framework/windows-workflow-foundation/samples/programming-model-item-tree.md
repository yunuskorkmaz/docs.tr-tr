---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 059bb3edcfe41f52e2244ff6f5bf3fc78a4262bb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235811"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="2fbb8-102">Programlama Modeli Öğe Ağacı</span><span class="sxs-lookup"><span data-stu-id="2fbb8-102">Programming Model Item Tree</span></span>

<span data-ttu-id="2fbb8-103">Bu örnek, <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veri bağlamayı kullanarak ağaçta nasıl gezineceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="2fbb8-104">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2fbb8-104">Sample Details</span></span>

 <span data-ttu-id="2fbb8-105"><xref:System.Activities.Presentation.Model.ModelItem>Ağaç, düzenlenen temeldeki örnekle ilgili verileri göstermek Için Windows iş akışı Tasarımcısı altyapısı tarafından kullanılan soyutlamadır.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="2fbb8-106">Aşağıdaki çizim İş Akışı Tasarımcısı içindeki çeşitli altyapı katmanlarının bir gösterimi.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="2fbb8-108"><xref:System.Activities.Presentation.Model.ModelItem>, Temel alınan değerin bir işaretçisinin yanı sıra bir nesne koleksiyonu içerir <xref:System.Activities.Presentation.Model.ModelProperty> .</span><span class="sxs-lookup"><span data-stu-id="2fbb8-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="2fbb8-109"><xref:System.Activities.Presentation.Model.ModelProperty>Sırasıyla bir nesne, özelliğin adı ve türü gibi verilerden oluşur ve sonra değer için bir işaretçi, diğeri de olur <xref:System.Activities.Presentation.Model.ModelItem> .</span><span class="sxs-lookup"><span data-stu-id="2fbb8-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="2fbb8-110">Bir değer Dönüştürücüsü, <xref:System.Activities.Presentation.Model.ModelItem> <xref:System.Activities.Presentation.Model.ModelProperty> ağaç görünümünde doğru görünmesini sağlamak için bir öğesinden döndürülen bazı öğeleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="2fbb8-111">Örnek daha sonra, <xref:System.Activities.Presentation.Model.ModelItem> Aşağıdaki örnekte görüldüğü gibi, zorunlu sözdizimini kullanarak nasıl imperatively program ağacına karşılık gelen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="2fbb8-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="2fbb8-112">To use this sample</span></span>

1. <span data-ttu-id="2fbb8-113">Visual Studio 2010 ' de Studio. sln çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="2fbb8-114">**Build** menüsünden **Build Solution** ' i seçerek çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="2fbb8-115">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-115">Press F5 to run the application.</span></span> <span data-ttu-id="2fbb8-116">WPF formu daha sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="2fbb8-117">Yüklemek ve ağaç görünümüne bağlamak için **WF yükle** düğmesine tıklayın <xref:System.Activities.Presentation.Model.ModelItem> .</span><span class="sxs-lookup"><span data-stu-id="2fbb8-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="2fbb8-118">**Model öğe ağacını Değiştir** düğmesine tıklamak, bir öğeyi ağaca eklemek ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fbb8-119">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2fbb8-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2fbb8-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2fbb8-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fbb8-122">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="2fbb8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
