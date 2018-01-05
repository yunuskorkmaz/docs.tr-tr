---
title: "Görünüm durumu Tasarımcı kaldırma bir XAML dosyasına ekler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da4423b5f6106bde106de739a8a33e351d17c3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="b7186-102">Görünüm durumu Tasarımcı kaldırma bir XAML dosyasına ekler</span><span class="sxs-lookup"><span data-stu-id="b7186-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="b7186-103">Bu örnek türeyen bir sınıf oluşturmak nasıl gösterir <xref:System.Windows.Markup.XamlWriter> ve kaldırır XAML dosyası durumunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b7186-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="b7186-104">Görünüm durumu bilinen XAML belgesine bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="b7186-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="b7186-105">Görünüm durumu, çalışma zamanında gerekli olmayan düzen konumlandırma gibi tasarım zamanında, gerekli olan bilgileri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b7186-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="b7186-106">Bu bilgiler, düzenlenebilir XAML belgeye ekler.</span><span class="sxs-lookup"><span data-stu-id="b7186-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="b7186-107">Görünüm durumu ile XAML dosyası Yazar `mc:Ignorable` XAML dosyası çalışma zamanı yüklediğinde, bu bilgileri yüklenmedi şekilde özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b7186-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="b7186-108">Bu örnek XAML düğümleri işlerken, Görünüm durumu bilgisini kaldırır bir sınıfın nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7186-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b7186-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="b7186-109">Discussion</span></span>  
 <span data-ttu-id="b7186-110">Bu örnek nasıl özel bir yazıcı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7186-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="b7186-111">Özel bir XAML yazıcısı oluşturmak için öğesinden devralınan bir sınıf oluşturmanız <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b7186-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="b7186-112">XAML yazıcılar genellikle içe gibi bir "İç" XAML yazıcı izlemek için normaldir.</span><span class="sxs-lookup"><span data-stu-id="b7186-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="b7186-113">Bu "İç ' yazıcılarının zorlayıcı iş ve işleme yığını geri kalanı için temsilci seçme için birden çok giriş noktası olmasını sağlayarak XAML yazıcılarının kalan yığınını başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="b7186-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="b7186-114">Bu örnekte, ilgi birkaç öğe yok.</span><span class="sxs-lookup"><span data-stu-id="b7186-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="b7186-115">Yazılmakta öğesi Tasarımcı Ad alanından olup olmadığını görmek için onay biridir.</span><span class="sxs-lookup"><span data-stu-id="b7186-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="b7186-116">Bu ayrıca diğer türlerinin bir iş akışında Tasarımcı Ad alanından çıkışı şeritler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b7186-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="b7186-117">Bu aynı zamanda bir yığın düğümü akışı geçişi sırasında kullanılan XAML üyelerinin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7186-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="b7186-118">Bu örnek, kalan çalışma büyük ölçüde yer <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7186-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
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
  
 <span data-ttu-id="b7186-119">Sonraki yöntemleri sonra bunlar hala bir görünüm durumu kapsayıcıda bulunan olup olmadığını denetleyin ve gerekiyorsa, dönün ve yazıcı yığın aşağı düğümü geçmeyin.</span><span class="sxs-lookup"><span data-stu-id="b7186-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
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
  
 <span data-ttu-id="b7186-120">Özel bir XAML yazan kullanmak için onu XAML yazıcılarının yığınında zincir gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7186-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="b7186-121">Aşağıdaki kod bu nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7186-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b7186-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b7186-122">To use this sample</span></span>  
  
1. <span data-ttu-id="b7186-123">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ViewStateCleaningWriter.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b7186-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="b7186-124">Bir komut istemi açın ve burada ViewStageCleaningWriter.exe yerleşik dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="b7186-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="b7186-125">ViewStateCleaningWriter.exe Workflow1.xaml dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7186-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="b7186-126">Yürütülebilir dosya için sözdizimi aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b7186-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="b7186-127">Bu bir XAML dosyasına çıkarır \[çıkışdosyası], kaldırılan tüm görünüm durum bilgilerini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b7186-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7186-128">İçin bir <xref:System.Activities.Statements.Sequence> iş akışı, bir dizi sanallaştırma ipuçları kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b7186-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="b7186-129">Bu, düzeni yüklendiği sonraki sefer yeniden hesaplamak Tasarımcı neden olur.</span><span class="sxs-lookup"><span data-stu-id="b7186-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="b7186-130">Bu örnek için kullandığınızda, bir <xref:System.Activities.Statements.Flowchart>, tüm konumlandırma ve yönlendirme bilgilerini satır kaldırılır ve ekranın sol tarafındaki Yığılmış Tasarımcı içine sonraki yüklemeyi, tüm etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b7186-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="b7186-131">Bu örnek ile kullanmak için bir örnek XAML dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b7186-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="b7186-132">Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7186-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="b7186-133">Yeni bir iş akışı konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7186-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="b7186-134">Birkaç etkinlikleri tuvale sürükleyip</span><span class="sxs-lookup"><span data-stu-id="b7186-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="b7186-135">İş akışı XAML dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b7186-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="b7186-136">Ekli özellikler durumunu görmek için XAML dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="b7186-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7186-137">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7186-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7186-138">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b7186-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b7186-139">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b7186-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7186-140">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b7186-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
