---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038179"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="c9d18-102">Programlama Modeli Öğe Ağacı</span><span class="sxs-lookup"><span data-stu-id="c9d18-102">Programming Model Item Tree</span></span>
<span data-ttu-id="c9d18-103">Bu örnek, <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veri bağlamayı kullanarak ağaçta nasıl gezineceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9d18-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="c9d18-104">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c9d18-104">Sample Details</span></span>
 <span data-ttu-id="c9d18-105">Ağaç, düzenlenmekte olan temeldeki örnekle ilgili verileri göstermek için [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] altyapı tarafından kullanılan soyutlamadır. <xref:System.Activities.Presentation.Model.ModelItem></span><span class="sxs-lookup"><span data-stu-id="c9d18-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="c9d18-106">Aşağıdaki çizim, [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]içindeki çeşitli altyapı katmanlarının bir gösterimi.</span><span class="sxs-lookup"><span data-stu-id="c9d18-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="c9d18-108">, Temel alınan değerin bir işaretçisinin yanı sıra bir <xref:System.Activities.Presentation.Model.ModelProperty> nesne koleksiyonu içerir.<xref:System.Activities.Presentation.Model.ModelItem></span><span class="sxs-lookup"><span data-stu-id="c9d18-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="c9d18-109">Sırasıyla <xref:System.Activities.Presentation.Model.ModelProperty> bir nesne, özelliğin adı ve türü gibi verilerden oluşur ve sonra değer için bir işaretçi, diğeri <xref:System.Activities.Presentation.Model.ModelItem>de olur.</span><span class="sxs-lookup"><span data-stu-id="c9d18-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="c9d18-110">Bir değer Dönüştürücüsü, ağaç görünümünde doğru görünmesini sağlamak için <xref:System.Activities.Presentation.Model.ModelItem>bir <xref:System.Activities.Presentation.Model.ModelProperty> öğesinden döndürülen bazı öğeleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9d18-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="c9d18-111">Örnek daha sonra, aşağıdaki örnekte görüldüğü gibi, zorunlu <xref:System.Activities.Presentation.Model.ModelItem> sözdizimini kullanarak nasıl imperatively program ağacına karşılık gelen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9d18-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="c9d18-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c9d18-112">To use this sample</span></span>

1. <span data-ttu-id="c9d18-113">Visual Studio 2010 ' de Studio. sln çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="c9d18-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="c9d18-114">**Build** menüsünden **Build Solution** ' i seçerek çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9d18-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="c9d18-115">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="c9d18-115">Press F5 to run the application.</span></span> <span data-ttu-id="c9d18-116">WPF formu daha sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9d18-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="c9d18-117">Yüklemek<xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlamak için **WF yükle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9d18-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="c9d18-118">**Model öğe ağacını Değiştir** düğmesine tıklamak, bir öğeyi ağaca eklemek ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="c9d18-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9d18-119">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9d18-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c9d18-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c9d18-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c9d18-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="c9d18-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9d18-122">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c9d18-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="c9d18-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9d18-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
