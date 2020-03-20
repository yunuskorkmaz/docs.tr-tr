---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142699"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="39b34-102">Programlama Modeli Öğe Ağacı</span><span class="sxs-lookup"><span data-stu-id="39b34-102">Programming Model Item Tree</span></span>
<span data-ttu-id="39b34-103">Bu örnek, Windows Sunu <xref:System.Activities.Presentation.Model.ModelItem> Temeli (WPF) Ağaç Görünümü'nden bildirimsel veri bağlamakullanarak ağaçta nasıl gezinilince gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39b34-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="39b34-104">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="39b34-104">Sample Details</span></span>
 <span data-ttu-id="39b34-105">Ağaç, <xref:System.Activities.Presentation.Model.ModelItem> Windows İş Akışı Tasarımcısı altyapısı tarafından, düzenlenen temel örnekle ilgili verileri ortaya çıkarmak için kullanılan soyutlamadır.</span><span class="sxs-lookup"><span data-stu-id="39b34-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="39b34-106">Aşağıdaki resimde, İş Akışı Tasarımcısı içindeki çeşitli altyapı katmanlarının bir tasviri ve</span><span class="sxs-lookup"><span data-stu-id="39b34-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="39b34-108">A, <xref:System.Activities.Presentation.Model.ModelItem> temel değere işaretçi nin yanı sıra <xref:System.Activities.Presentation.Model.ModelProperty> nesneler koleksiyonundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="39b34-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="39b34-109">Sırayla bir <xref:System.Activities.Presentation.Model.ModelProperty> nesne, adı ve özelliğinin türü gibi verilerden oluşur ve sonra değer için <xref:System.Activities.Presentation.Model.ModelItem>bir işaretçi, sırayla, başka bir .</span><span class="sxs-lookup"><span data-stu-id="39b34-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="39b34-110">Değer dönüştürücü, a'dan <xref:System.Activities.Presentation.Model.ModelItem> <xref:System.Activities.Presentation.Model.ModelProperty> döndürülen bazı s'leri işlemek için kullanılır ve ağaç görünümünde doğru görünmelerini sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39b34-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="39b34-111">Örnek daha sonra aşağıdaki örnekte görüldüğü <xref:System.Activities.Presentation.Model.ModelItem> gibi, zorunlu sözdizimini kullanarak ağaca karşı zorunlu olarak nasıl programlanırgösteriz.</span><span class="sxs-lookup"><span data-stu-id="39b34-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="39b34-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="39b34-112">To use this sample</span></span>

1. <span data-ttu-id="39b34-113">Visual Studio 2010'da ProgrammingModelItemTree.sln çözümlerini açın.</span><span class="sxs-lookup"><span data-stu-id="39b34-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="39b34-114">**Yapı** menüsünden **Çözüm Oluştur'u** seçerek çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39b34-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="39b34-115">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="39b34-115">Press F5 to run the application.</span></span> <span data-ttu-id="39b34-116">WPF formu daha sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="39b34-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="39b34-117">Yüklemek <xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlamak için **WF** Yükle düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="39b34-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="39b34-118">**Model Öğesi Ağacını Değiştir** düğmesini tıklattığınızda, ağaca bir öğe eklemek ve bir özellik ayarlamak için önceki kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="39b34-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39b34-119">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="39b34-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="39b34-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="39b34-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="39b34-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="39b34-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39b34-122">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="39b34-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="39b34-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39b34-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
