---
title: Tasarımcı görünüm durumunu kaldırma bir XAML dosyasına eklediği
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: 0d4dccb16796893df58f709e011657457cc71670
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835726"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="ab6a0-102">Tasarımcı görünüm durumunu kaldırma bir XAML dosyasına eklediği</span><span class="sxs-lookup"><span data-stu-id="ab6a0-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="ab6a0-103">Bu örnek, türetilen bir sınıf oluşturmak nasıl gösterir <xref:System.Windows.Markup.XamlWriter> ve kaldırır bir XAML dosyası durumunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] <span data-ttu-id="ab6a0-104">Görünüm durumu bilinen XAML belgesine bilgilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="ab6a0-105">Görünüm durumu çalışma zamanında gerekli değildir yerleşim konumlandırma gibi tasarım zamanında gerekli olan bilgileri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] <span data-ttu-id="ab6a0-106">Bu bilgiler düzenlemiş XAML belgeye ekler.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] <span data-ttu-id="ab6a0-107">Görünüm durumu ile XAML dosyasına yazar `mc:Ignorable` özniteliği için çalışma zamanı XAML dosya yüklendiğinde bu bilgileri yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="ab6a0-108">Bu örnek, Görünüm durumu bilgilerinin XAML düğümleri işlenirken kaldıran bir sınıf oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="ab6a0-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="ab6a0-109">Discussion</span></span>
 <span data-ttu-id="ab6a0-110">Bu örnek, özel bir yazıcı oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-110">This sample demonstrates how to create a custom writer.</span></span>

 <span data-ttu-id="ab6a0-111">Özel bir XAML yazıcısı oluşturmak için devralınan bir sınıf oluşturma <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="ab6a0-112">XAML yazıcılar genellikle iç içe gibi "İç" bir XAML yazıcı izlemek için tipik bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="ab6a0-113">Bu "İç ' yazıcılar düşünülebilir çalışmak ve sonra işleme yığını geri kalanı için temsilci seçmek için birden çok giriş noktası olmasını sağlayarak, XAML yazıcılar kalan yığın başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

 <span data-ttu-id="ab6a0-114">Bu örnekte, ilgilenilen birkaç öğe yok.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="ab6a0-115">Yazılmakta olan öğe bir tasarımcı ad alanından olup olmadığını görmek için onay biridir.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="ab6a0-116">Bu da bir iş akışında Tasarımcı ad alanı diğer türlerden kullanımını göz şeritler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

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

 <span data-ttu-id="ab6a0-117">Bu aynı zamanda bir yığın düğümü akışı geçişi sırasında kullanılan XAML üyelerinin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="ab6a0-118">Bu örnek, kalan iş büyük ölçüde bulunan <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>

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

 <span data-ttu-id="ab6a0-119">Sonraki yöntem sonra bunlar yine de bir görünüm durumu kapsayıcıda bulunan olup olmadığını denetleyin ve bu durumda, dönüş ve yazıcı yığın düğüm geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

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

 <span data-ttu-id="ab6a0-120">Özel bir XAML yazıcı kullanmak için bu XAML yazıcılar yığında zincir gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="ab6a0-121">Aşağıdaki kod bunu nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="ab6a0-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ab6a0-122">To use this sample</span></span>

1. <span data-ttu-id="ab6a0-123">Visual Studio 2010 kullanarak ViewStateCleaningWriter.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="ab6a0-124">Bir komut istemi açın ve burada ViewStageCleaningWriter.exe oluşturulmuştur dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="ab6a0-125">ViewStateCleaningWriter.exe Workflow1.xaml dosya üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="ab6a0-126">Yürütülebilir dosya için söz dizimi aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="ab6a0-127">Bu bir XAML dosyasına çıkarır \[outfile], sahip olduğu tüm görünüm durumu bilgilerini kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="ab6a0-128">İçin bir <xref:System.Activities.Statements.Sequence> iş akışı, bir dizi sanallaştırma ipuçları kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="ab6a0-129">Bu, sonraki yüklendiğinde düzenini yeniden hesapla Tasarımcı neden olur.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="ab6a0-130">Bu örnek için kullandığınızda bir <xref:System.Activities.Statements.Flowchart>, tüm konumlandırma ve yönlendirme bilgilerini satır kaldırılır ve ekranın sol tarafında yığılma Tasarımcı içinde sonraki yüklemeyi, tüm etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="ab6a0-131">Bu örnek ile kullanmak için örnek bir XAML dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ab6a0-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="ab6a0-132">Visual Studio 2010'u açın.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="ab6a0-133">Yeni bir iş akışı konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="ab6a0-134">Sürükle ve bırak tuvale birkaç etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="ab6a0-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="ab6a0-135">İş akışı XAML dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="ab6a0-136">Ekli özellikler durumunu görmek için XAML dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab6a0-137">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab6a0-138">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ab6a0-139">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab6a0-140">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ab6a0-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
