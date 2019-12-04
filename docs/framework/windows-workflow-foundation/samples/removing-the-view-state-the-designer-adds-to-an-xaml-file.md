---
title: Tasarımcı bir XAML dosyasına eklediği görünüm durumunu kaldırma-WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715616"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="1ab82-102">Tasarımcı bir XAML dosyasına eklediği görünüm durumunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="1ab82-102">Removing the view state the designer adds to an XAML file</span></span>

<span data-ttu-id="1ab82-103">Bu örnek, <xref:System.Xaml.XamlWriter> türetilen ve bir XAML dosyasından görünüm durumunu kaldıran bir sınıfın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-103">This sample demonstrates how to create a class that derives from <xref:System.Xaml.XamlWriter> and removes view state from a XAML file.</span></span> <span data-ttu-id="1ab82-104">Windows İş Akışı Tasarımcısı, görüntüleme durumu olarak bilinen XAML belgesine bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="1ab82-104">Windows Workflow Designer writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="1ab82-105">Görünüm durumu, çalışma zamanında gerekli olmayan, tasarım zamanında (düzen konumlandırma gibi) gerekli olan bilgilere başvurur.</span><span class="sxs-lookup"><span data-stu-id="1ab82-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> <span data-ttu-id="1ab82-106">İş Akışı Tasarımcısı, bu bilgileri XAML belgesine düzenlendiğinden ekler.</span><span class="sxs-lookup"><span data-stu-id="1ab82-106">Workflow Designer inserts this information into the XAML document as it is edited.</span></span> <span data-ttu-id="1ab82-107">İş Akışı Tasarımcısı, görünüm durumunu XAML dosyasına `mc:Ignorable` özniteliğiyle yazar, bu nedenle çalışma zamanı XAML dosyasını yüklediğinde bu bilgiler yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="1ab82-107">Workflow Designer writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="1ab82-108">Bu örnek, XAML düğümlerini işlerken görünüm durumu bilgisini kaldıran bir sınıfın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="1ab82-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="1ab82-109">Discussion</span></span>

<span data-ttu-id="1ab82-110">Bu örnek, özel bir yazıcı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-110">This sample demonstrates how to create a custom writer.</span></span>

<span data-ttu-id="1ab82-111">Özel bir XAML yazıcısı oluşturmak için <xref:System.Xaml.XamlWriter>devralan bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ab82-111">To build a custom XAML writer, create a class that inherits from <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="1ab82-112">XAML yazarları genellikle iç içe geçmişse, "iç" XAML yazıcısının izlenmesi tipik bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="1ab82-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="1ab82-113">Bu "iç" yazarlar, diğer XAML yazıcı yığınına başvuru olarak düşünülebilir. böylece, iş yapmak için birden çok giriş noktasına sahip olabilirsiniz ve sonra yığının geri kalanına işleme atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ab82-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

<span data-ttu-id="1ab82-114">Bu örnekte, ilgilendiğiniz birkaç öğe vardır.</span><span class="sxs-lookup"><span data-stu-id="1ab82-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="1ab82-115">Bunlardan biri, yazılan öğenin tasarımcı ad alanından olup olmadığını görmekte olan bir denetim olur.</span><span class="sxs-lookup"><span data-stu-id="1ab82-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="1ab82-116">Bu Ayrıca, bir iş akışındaki tasarımcı ad alanından diğer türlerin kullanımını da kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1ab82-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

<span data-ttu-id="1ab82-117">Bu, düğüm akışından geçiş sırasında kullanılan XAML üyeleri yığınını da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ab82-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="1ab82-118">Bu örneğin kalan işi büyük ölçüde `WriteStartMember` yönteminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ab82-118">The remaining work of this sample is largely contained in the `WriteStartMember` method.</span></span>

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

<span data-ttu-id="1ab82-119">Sonraki Yöntemler bundan sonra bir görünüm durumu kapsayıcısında içerilip içerilmediğini kontrol eder ve istiyorsanız düğümü yazıcı yığınına geri geçirmez.</span><span class="sxs-lookup"><span data-stu-id="1ab82-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

<span data-ttu-id="1ab82-120">Özel bir XAML yazıcısını kullanmak için, XAML yazıcılarının bir yığınında birlikte zincirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="1ab82-121">Aşağıdaki kod, bunun nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a><span data-ttu-id="1ab82-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1ab82-122">To use this sample</span></span>

1. <span data-ttu-id="1ab82-123">Visual Studio 2010 kullanarak, ViewStateCleaningWriter. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1ab82-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="1ab82-124">Bir komut istemi açın ve Viewstagectaaningwriter. exe ' nin oluşturulduğu dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="1ab82-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="1ab82-125">Workflow1. xaml dosyasında ViewStateCleaningWriter. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1ab82-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="1ab82-126">Yürütülebilir dosya için sözdizimi aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="1ab82-127">Bu, tüm görünüm durumu bilgilerini kaldıran \[çıkışdosyası] öğesine bir XAML dosyası verir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="1ab82-128"><xref:System.Activities.Statements.Sequence> bir iş akışı için bir dizi sanallaştırma ipucu kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1ab82-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="1ab82-129">Bu, tasarımcının bir sonraki yüklenilişinde düzeni yeniden hesaplamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ab82-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="1ab82-130">Bu örneği bir <xref:System.Activities.Statements.Flowchart>için kullandığınızda, tüm konumlandırma ve çizgi yönlendirme bilgileri kaldırılır ve tasarımcı 'ya sonraki yükleme sırasında tüm etkinlikler ekranın sol tarafında yığılır.</span><span class="sxs-lookup"><span data-stu-id="1ab82-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="1ab82-131">Bu örnekle kullanılacak örnek bir XAML dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1ab82-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="1ab82-132">Visual Studio 2010 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1ab82-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="1ab82-133">Yeni bir Iş akışı konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ab82-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="1ab82-134">Birkaç etkinliği tuval üzerine sürükleyip bırakın</span><span class="sxs-lookup"><span data-stu-id="1ab82-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="1ab82-135">İş akışı XAML dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1ab82-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="1ab82-136">Görünüm durumu ekli özelliklerini görmek için XAML dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1ab82-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ab82-137">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ab82-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1ab82-138">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1ab82-138">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1ab82-139">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="1ab82-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1ab82-140">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ab82-140">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
