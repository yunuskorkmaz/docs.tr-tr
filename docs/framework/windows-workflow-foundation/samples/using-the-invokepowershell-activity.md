---
title: Invokepowershell etkinliğini kullanma
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269208"
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="52f5f-102">Invokepowershell etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="52f5f-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="52f5f-103">Invokepowershell örnek Windows PowerShell komutlarını kullanarak çağırmak nasıl gösterir `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="52f5f-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="52f5f-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="52f5f-105">Windows PowerShell komutlarının basit yenilik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="52f5f-106">Windows PowerShell çıkış hattından değerleri almak ve iş akışı değişkenleri depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52f5f-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="52f5f-107">Verileri, windows PowerShell ile bir yürütme komutu için giriş potansiyel olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52f5f-108">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="52f5f-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52f5f-109">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="52f5f-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52f5f-110">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="52f5f-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52f5f-111">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="52f5f-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="52f5f-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="52f5f-112">Discussion</span></span>  
 <span data-ttu-id="52f5f-113">Bu örnek, aşağıdaki üç projeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="52f5f-114">Proje adı</span><span class="sxs-lookup"><span data-stu-id="52f5f-114">Project Name</span></span>|<span data-ttu-id="52f5f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52f5f-115">Description</span></span>|<span data-ttu-id="52f5f-116">Ana dosyaları</span><span class="sxs-lookup"><span data-stu-id="52f5f-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="52f5f-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="52f5f-117">CodedClient</span></span>|<span data-ttu-id="52f5f-118">PowerShell etkinliğini kullanan örnek istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="52f5f-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="52f5f-119">-   **Program.cs**: program aracılığıyla Invokepowershell etkinliğini çağıran bir dizisi tabanlı bir iş akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52f5f-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="52f5f-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="52f5f-120">DesignerClient</span></span>|<span data-ttu-id="52f5f-121">Bir dizi içeren özel etkinlikler `InvokePowerShell` özel etkinlik ve diğer çeşitli özel etkinlikler ve bunları kullanan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="52f5f-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="52f5f-122">Etkinlikleri:</span><span class="sxs-lookup"><span data-stu-id="52f5f-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="52f5f-123">**PrintCollection.cs**: konsola bir koleksiyondaki tüm öğeleri yazdıran Yardımcısı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="52f5f-124">**ReadLine.cs**: konsoldan okuma giriş için bir yardımcı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="52f5f-125">Dosya sistemi:</span><span class="sxs-lookup"><span data-stu-id="52f5f-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="52f5f-126">**Copy.XAML**: bir dosyayı kopyalar bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="52f5f-127">**CreateFile.xaml**: aktivite bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52f5f-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="52f5f-128">**DeleteFile.xaml**: bir dosyayı silen bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="52f5f-129">**MakeDir.xaml**: bir dizin oluşturan bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="52f5f-130">**Move.XAML**: bir dosyayı taşır bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="52f5f-131">**ReadFile.xaml**: bir dosyayı okur ve içeriği döndüren bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="52f5f-132">**TestPath.xaml**: yol varlığını test eden bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="52f5f-133">İşlem:</span><span class="sxs-lookup"><span data-stu-id="52f5f-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="52f5f-134">**GetProcess.xaml**: aktivite çalışan işlemlerin bir listesi alır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="52f5f-135">**StopProcess.xaml**: belirli bir işlem durduran bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="52f5f-136">**Program.cs**: Sıra1 iş akışını çağırır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="52f5f-137">**Sequence1.XAML**: sırası tabanlı bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="52f5f-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="52f5f-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="52f5f-138">PowerShell</span></span>|<span data-ttu-id="52f5f-139">`InvokePowerShell` Etkinlik ve onun ilişkili tasarımcıları.</span><span class="sxs-lookup"><span data-stu-id="52f5f-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="52f5f-140">Etkinlik dosyaları</span><span class="sxs-lookup"><span data-stu-id="52f5f-140">Activity Files</span></span><br /><br /> <span data-ttu-id="52f5f-141">-   **ExecutePowerShell.cs**: etkinliğinin ana yürütme mantığı.</span><span class="sxs-lookup"><span data-stu-id="52f5f-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="52f5f-142">-   **InvokePowerShell.cs**: Genel (dönüş değeri) sürümü ve genel olmayan (dönüş değeri) sürümü içeren ana yürütme mantığı çevresinde bir sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="52f5f-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="52f5f-143">Bu etkinlik için ortak arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="52f5f-144">-   **NoPersistZone.cs**: Bu etkinlik herhangi bir alt etkinlik kalıcı engeller.</span><span class="sxs-lookup"><span data-stu-id="52f5f-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="52f5f-145">Bu sınıf içinde kullanılan `InvokePowerShell` etkinliği engellemek için etkinlik uygulaması kalıcı Orta yürütme.</span><span class="sxs-lookup"><span data-stu-id="52f5f-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="52f5f-146">Tasarımcı dosyaları:</span><span class="sxs-lookup"><span data-stu-id="52f5f-146">Designer files:</span></span><br /><br /> <span data-ttu-id="52f5f-147">1.  **ArgumentDictionaryEditor.cs**: bağımsız değişkenleri düzenlemek kullanıcıya izin veren bir Windows iletişim `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="52f5f-148">2.  **GenericInvokePowerShellDesigner.xaml** ve **GenericInvokePowerShellDesigner.xaml.cs**: genel görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52f5f-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="52f5f-149">3.  **InvokePowerShellDesigner.xaml** ve **InvokePowerShellDesigner.cs**: genel olmayan görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52f5f-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="52f5f-150">İstemci projeleri kullanımını anlaşıldıktan sonra PowerShell etkinlik iç işlevleri anlamak daha kolay olsa da ilk olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="52f5f-151">Bu örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="52f5f-151">Using This Sample</span></span>  
 <span data-ttu-id="52f5f-152">Aşağıdaki bölümlerde, üç projelerinin örnekte nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="52f5f-153">Kodlanmış istemci projesi kullanma</span><span class="sxs-lookup"><span data-stu-id="52f5f-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="52f5f-154">Örnek istemci programlı olarak kullanmanın birkaç farklı yöntem örneklerini içeren bir sıralama etkinliği oluşturur `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="52f5f-155">Not defterini ilk çağrı başlatır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="52f5f-156">İkinci çağrı yerel makine üzerinde çalışan işlemlerin bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="52f5f-157">`Output` değişkeni komutunun çıktısını depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="52f5f-158">Sonraki çağrı, tek tek her PowerShell çağırma çıktıda bir sonradan işleme adımı çalıştırılacak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="52f5f-159">`InitializationAction` Her işlem için dize gösterimini çıkarır işlevi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="52f5f-160">Bu dizeler koleksiyonu döndürülür `Output` değişkenini `InvokePowerShell<string>` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="52f5f-161">Başarılı `InvokePowerShell` çağrılarını göstermek veri geçirme etkinliği ve çıktıları ve hataları alınıyor.</span><span class="sxs-lookup"><span data-stu-id="52f5f-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="52f5f-162">Tasarımcı istemci projesi kullanma</span><span class="sxs-lookup"><span data-stu-id="52f5f-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="52f5f-163">Özel etkinlikler, neredeyse her biri yerleşik içeren bir dizi DesignerClient proje oluşur `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="52f5f-164">Çoğu etkinliklerinin genel olmayan sürümü, çağrı `InvokePowerShell` etkinliği ve bir dönüş değeri beklemiyoruz.</span><span class="sxs-lookup"><span data-stu-id="52f5f-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="52f5f-165">Diğer etkinlikler genel kullanmanız `InvokePowerShell` etkinliği ve kullanım `InitializationAction` sonuçları sonrası işlemek için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="52f5f-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="52f5f-166">PowerShell projesine kullanma</span><span class="sxs-lookup"><span data-stu-id="52f5f-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="52f5f-167">Ana eylem etkinlik gerçekleştikten `ExecutePowerShell` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="52f5f-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="52f5f-168">PowerShell komutların yürütülmesini temel iş akışı iş parçacığı engellemelisiniz değil çünkü etkinlik devralarak zaman uyumsuz bir etkinlik olması oluşturulur <xref:System.Activities.AsyncCodeActivity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="52f5f-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="52f5f-169"><xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Yöntemi etkinlik çalıştırmaya başlamak için iş akışı çalışma zamanı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="52f5f-170">PowerShell işlem hattını oluşturmak için PowerShell API'lerini çağırarak başlar.</span><span class="sxs-lookup"><span data-stu-id="52f5f-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="52f5f-171">Bir PowerShell komut oluşturur ve parametreler ve değişkenler ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="52f5f-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="52f5f-172">İçinde yöneltilen girişleri de bu noktada işlem hattının gönderilir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="52f5f-173">Son olarak, işlem hattı içinde sarmalanmış bir `PipelineInvokerAsyncResult` nesne ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="52f5f-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="52f5f-174">`PipelineInvokerAsyncResult` Nesne dinleyicisi kaydeder ve işlem hattı çağırır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="52f5f-175">Yürütme sona erdiğinde çıktısının ve hataların aynı içinde depolanan `PipelineInvokerAsyncResult` nesne ve denetim devredildiği geri akışı çalışma zamanı için ilk olarak geçirilen geri çağırma yöntemi çağırarak <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span><span class="sxs-lookup"><span data-stu-id="52f5f-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="52f5f-176">Yöntemin yürütülmesine sonunda, iş akışı çalışma zamanı etkinliğin çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52f5f-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="52f5f-177">`InvokePowerShell` Sınıfı sarar `ExecutePowerShellCommand` sınıfı ve etkinliği; genel bir sürümü iki sürümü ve genel olmayan sürümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52f5f-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="52f5f-178">Genel tür için tek tek sonuçları genel sürüm dönüştüren ise genel olmayan sürüm PowerShell yürütme çıkışını doğrudan döndürür.</span><span class="sxs-lookup"><span data-stu-id="52f5f-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="52f5f-179">Etkinliğin genel sürüm çağıran bir sıralı iş akışı uygulanan `ExecutePowerShellCommand` ve sonuçları sonrası işler.</span><span class="sxs-lookup"><span data-stu-id="52f5f-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="52f5f-180">Sonuç koleksiyondaki her öğe için işlem sonrası adımı çağırır `InitializationAction` ayarlanmış ise.</span><span class="sxs-lookup"><span data-stu-id="52f5f-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="52f5f-181">Aksi takdirde, basit bir tür dönüştürme yapar.</span><span class="sxs-lookup"><span data-stu-id="52f5f-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="52f5f-182">Her iki `InvokePowerShell` etkinlikleri (genel ve genel olmayan), bir tasarımcı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="52f5f-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="52f5f-183">InvokePowerShellDesigner.xaml ve ilişkili .cs dosyası görünümünü tanımlamak [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] genel olmayan sürümünün `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="52f5f-184">InvokePowerShellDesigner.xaml içinde bir <xref:System.Windows.Controls.DockPanel> grafik arabirimini temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52f5f-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="52f5f-185">Unutmayın `Text` özelliktir metin kutusunun etkinliğin değerini sağlar, iki yönlü bir bağlama `CommandText` özelliği, Tasarımcı değeri giriş eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="52f5f-186">GenericInvokePowerShellDesigner.xaml ve ilişkili .cs dosyası tanımlamak için genel grafik arabirim `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="52f5f-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="52f5f-187">Ayarlanacak kullanıcılar izin verdiğinden Tasarımcı biraz daha karmaşık bir `InitializationAction`.</span><span class="sxs-lookup"><span data-stu-id="52f5f-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="52f5f-188">Kullanımını anahtar öğedir <xref:System.Activities.Presentation.WorkflowItemPresenter> Sürükle izin vermek için ve bırakma bağımlı etkinliklerin `InvokePowerShell` Tasarımcı yüzeyine bırakın.</span><span class="sxs-lookup"><span data-stu-id="52f5f-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="52f5f-189">Tasarımcı özelleştirme tasarım tuvalde etkinlik görünümünü tanımlayan .xaml dosyalarını durdurmaz.</span><span class="sxs-lookup"><span data-stu-id="52f5f-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="52f5f-190">Etkinlik parametreleri görüntülemek için kullanılan iletişim kutuları da özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="52f5f-191">Bu parametreler ve PowerShell değişkenleri PowerShell komutlarını davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="52f5f-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="52f5f-192">Etkinlik olarak sunan <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` türleri.</span><span class="sxs-lookup"><span data-stu-id="52f5f-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="52f5f-193">Bu tür düzenlemenize olanak sağlayacak iletişim kutusu ArgumentDictionaryEditor.cs ve PropertyEditorResources.xaml PropertyEditorResources.cs tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52f5f-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52f5f-194">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="52f5f-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="52f5f-195">Bu örneği çalıştırmak için Windows PowerShell yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="52f5f-196">Windows PowerShell Bu konumdan yüklenebilir: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span><span class="sxs-lookup"><span data-stu-id="52f5f-196">Windows PowerShell can be installed from this location: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="52f5f-197">Kodlanmış istemciyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="52f5f-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="52f5f-198">Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52f5f-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="52f5f-199">Çözüme sağ tıklayın ve derleyin.</span><span class="sxs-lookup"><span data-stu-id="52f5f-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="52f5f-200">Sağ **CodedClient** seçin ve proje **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="52f5f-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="52f5f-201">Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="52f5f-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="52f5f-202">Tasarımcı istemciyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="52f5f-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="52f5f-203">Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52f5f-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="52f5f-204">Çözüme sağ tıklayın ve derleyin.</span><span class="sxs-lookup"><span data-stu-id="52f5f-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="52f5f-205">Sağ **DesignerClient** seçin ve proje **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="52f5f-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="52f5f-206">Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="52f5f-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="52f5f-207">Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="52f5f-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="52f5f-208">Başvuru değilse `InvokePowerShell` etkinlik derlemesini veya bir yapı hatası başka bir proje sonuçlarında projeden, el ile eklemeniz gerekebilir `<SpecificVersion>True</SpecificVersion>` başvurduğu satırı altında yeni projenin .csproj dosyasını bir öğeye `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="52f5f-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="52f5f-209">Windows PowerShell yüklü değilse, eklediğiniz hemen sonra aşağıdaki hata iletisini Visual Studio'da görüntülenir bir `InvokePowerShell` üzerine bir iş akışı etkinlik: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="52f5f-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="52f5f-210">Windows PowerShell 2.0 sürümünde, program aracılığıyla arama `$input.MoveNext()` başarısız olur ve betikleri kullanarak `$input.MoveNext()` istenmeyen hatalara ve sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="52f5f-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="52f5f-211">Bu sorunu geçici olarak çözmek için PowerShell fiili kullanmayı düşünün `foreach` çağırmak yerine `MoveNext()` bir dizi yineleme olduğunda.</span><span class="sxs-lookup"><span data-stu-id="52f5f-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52f5f-212">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="52f5f-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52f5f-213">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="52f5f-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52f5f-214">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="52f5f-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52f5f-215">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="52f5f-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`