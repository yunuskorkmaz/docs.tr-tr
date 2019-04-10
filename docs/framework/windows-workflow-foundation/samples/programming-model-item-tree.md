---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 1aaa1aa9922a7f57138782effe9492ec84198c8a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321139"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="092a4-102">Programlama Modeli Öğe Ağacı</span><span class="sxs-lookup"><span data-stu-id="092a4-102">Programming Model Item Tree</span></span>
<span data-ttu-id="092a4-103">Bu örnek nasıl gidileceğini gösteren <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veriler bağlama kullanarak ağaç.</span><span class="sxs-lookup"><span data-stu-id="092a4-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="092a4-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="092a4-104">Sample Details</span></span>
 <span data-ttu-id="092a4-105"><xref:System.Activities.Presentation.Model.ModelItem> Ağacıdır tarafından kullanılan soyutlama [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] düzenlenmekte olan temel örneği hakkındaki verileri göstermek için altyapı.</span><span class="sxs-lookup"><span data-stu-id="092a4-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="092a4-106">Aşağıdaki çizimde bir altyapı dahilinde çeşitli katmanları bir gösterimi olan [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="092a4-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="092a4-108">A <xref:System.Activities.Presentation.Model.ModelItem> koleksiyonunu yanı sıra, temeldeki değeri için bir işaretçi oluşur <xref:System.Activities.Presentation.Model.ModelProperty> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="092a4-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="092a4-109">A <xref:System.Activities.Presentation.Model.ModelProperty> nesnesi sırayla oluşur adı ve türü özelliği ve buna karşılık, başka değeri için bir işaretçi gibi veri <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="092a4-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="092a4-110">Bazılarını işlemek için kullanılan bir değer dönüştürücü <xref:System.Activities.Presentation.Model.ModelItem>s öğesinden döndürülen bir <xref:System.Activities.Presentation.Model.ModelProperty> hale getirmek için bunları doğru ağaç görünümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="092a4-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="092a4-111">Örnek daha sonra kesin karşı programlamak nasıl gösterir <xref:System.Activities.Presentation.Model.ModelItem> aşağıdaki örnekte görüldüğü gibi kesinlik temelli sözdizimi kullanılarak ağaç.</span><span class="sxs-lookup"><span data-stu-id="092a4-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="092a4-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="092a4-112">To use this sample</span></span>

1. <span data-ttu-id="092a4-113">Visual Studio 2010'da ProgrammingModelItemTree.sln çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="092a4-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="092a4-114">Çözüm seçerek yapı **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="092a4-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="092a4-115">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="092a4-115">Press F5 to run the application.</span></span> <span data-ttu-id="092a4-116">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Formu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="092a4-116">The [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] form is then displayed.</span></span>

4. <span data-ttu-id="092a4-117">Tıklayın **yük WF** yüklemek için düğmeye <xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlayın.</span><span class="sxs-lookup"><span data-stu-id="092a4-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="092a4-118">Tıklayarak **değişiklik modeli öğe ağacı** düğmesi ağacına bir öğe ekleyin ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="092a4-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="092a4-119">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="092a4-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="092a4-120">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="092a4-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="092a4-121">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="092a4-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="092a4-122">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="092a4-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="092a4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="092a4-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
