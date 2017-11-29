---
title: "InvokePowerShell etkinliğini kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23351ad32e608dc27b973691ec9a00fc2f94b3fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="a5341-102">InvokePowerShell etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="a5341-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="a5341-103">InvokePowerShell örnek Windows PowerShell komutlarını kullanarak çağrılacak gösterilmiştir `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a5341-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="a5341-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="a5341-105">Windows PowerShell komutlarının basit yenilik.</span><span class="sxs-lookup"><span data-stu-id="a5341-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="a5341-106">Windows PowerShell çıkış ardışık düzen değerleri almak ve iş akışı değişkenleri depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5341-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="a5341-107">Verileri windows PowerShell yürütme komut için giriş potansiyel olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="a5341-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5341-108">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a5341-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5341-109">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a5341-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a5341-110">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a5341-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5341-111">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a5341-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="a5341-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="a5341-112">Discussion</span></span>  
 <span data-ttu-id="a5341-113">Bu örnek, aşağıdaki üç projeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a5341-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="a5341-114">Proje adı</span><span class="sxs-lookup"><span data-stu-id="a5341-114">Project Name</span></span>|<span data-ttu-id="a5341-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5341-115">Description</span></span>|<span data-ttu-id="a5341-116">Ana dosyaları</span><span class="sxs-lookup"><span data-stu-id="a5341-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="a5341-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="a5341-117">CodedClient</span></span>|<span data-ttu-id="a5341-118">PowerShell etkinliği kullanan bir örnek istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a5341-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="a5341-119">-   **Program.cs**: program aracılığıyla InvokePowerShell etkinlik çağıran bir sıra tabanlı bir iş akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5341-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="a5341-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="a5341-120">DesignerClient</span></span>|<span data-ttu-id="a5341-121">İçeren özel etkinlikler kümesi `InvokePowerShell` özel etkinlik ve çeşitli diğer özel etkinlikler ve bunları kullanan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="a5341-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="a5341-122">Etkinlikleri:</span><span class="sxs-lookup"><span data-stu-id="a5341-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="a5341-123">**PrintCollection.cs**: konsoluna bir koleksiyondaki tüm öğeleri yazdırır Yardımcısı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="a5341-124">**ReadLine.cs**: konsoldan okuma girişi için bir yardımcı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="a5341-125">Dosya sistemi:</span><span class="sxs-lookup"><span data-stu-id="a5341-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="a5341-126">**Copy.XAML**: bir dosya kopyalayan bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="a5341-127">**CreateFile.xaml**: aktivite bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5341-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="a5341-128">**DeleteFile.xaml**: bir dosyayı siler bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="a5341-129">**MakeDir.xaml**: bir dizin oluşturan bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="a5341-130">**Move.XAML**: bir dosyayı taşır bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="a5341-131">**ReadFile.xaml**: bir dosyayı okur ve içeriği döndüren bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="a5341-132">**TestPath.xaml**: bir yol varlığını testleri bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="a5341-133">İşlem:</span><span class="sxs-lookup"><span data-stu-id="a5341-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="a5341-134">**GetProcess.xaml**: aktivite çalışan işlemlerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="a5341-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="a5341-135">**StopProcess.xaml**: belirli bir işlemi durdurur bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="a5341-136">**Program.cs**: Sıra1 iş akışını çağırır.</span><span class="sxs-lookup"><span data-stu-id="a5341-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="a5341-137">**Sequence1.XAML**: dizisi tabanlı bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="a5341-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="a5341-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5341-138">PowerShell</span></span>|<span data-ttu-id="a5341-139">`InvokePowerShell` Etkinliği ve onun ilişkili tasarımcıları.</span><span class="sxs-lookup"><span data-stu-id="a5341-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="a5341-140">Etkinlik dosyaları</span><span class="sxs-lookup"><span data-stu-id="a5341-140">Activity Files</span></span><br /><br /> <span data-ttu-id="a5341-141">-   **ExecutePowerShell.cs**: ana yürütme mantığını etkinliği.</span><span class="sxs-lookup"><span data-stu-id="a5341-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="a5341-142">-   **InvokePowerShell.cs**: bir genel (dönüş değeri) sürümü ve genel olmayan (dönüş değeri) sürümü içeren ana yürütme mantığı çevresinde sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="a5341-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="a5341-143">Bu etkinlik için ortak arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="a5341-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="a5341-144">-   **NoPersistZone.cs**: kalıcı gelen tüm alt etkinlikler bu etkinliği engeller.</span><span class="sxs-lookup"><span data-stu-id="a5341-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="a5341-145">Bu sınıf içinde kullanılan `InvokePowerShell` etkinlik engellemek için etkinlik uygulama kalıcı Orta yürütme.</span><span class="sxs-lookup"><span data-stu-id="a5341-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="a5341-146">Tasarımcı dosyalar:</span><span class="sxs-lookup"><span data-stu-id="a5341-146">Designer files:</span></span><br /><br /> <span data-ttu-id="a5341-147">1.  **ArgumentDictionaryEditor.cs**: bağımsız değişkenleri düzenlemesine olanak tanır bir Windows iletişim `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="a5341-148">2.  **GenericInvokePowerShellDesigner.xaml** ve **GenericInvokePowerShellDesigner.xaml.cs**: genel görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5341-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="a5341-149">3.  **InvokePowerShellDesigner.xaml** ve **InvokePowerShellDesigner.cs**: genel olmayan görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5341-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="a5341-150">Kullanımı anladım sonra PowerShell etkinlik iç işlevleri anlamak daha kolay olduğundan istemci projeleri ilk olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a5341-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="a5341-151">Bu örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="a5341-151">Using This Sample</span></span>  
 <span data-ttu-id="a5341-152">Aşağıdaki bölümlerde üç projelerinin örnekte nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5341-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="a5341-153">Kodlanmış istemci projesi kullanma</span><span class="sxs-lookup"><span data-stu-id="a5341-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="a5341-154">Örnek istemci programlı olarak kullanmanın birkaç farklı yöntem örnekleri içeren bir sıralı etkinlik oluşturur `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="a5341-155">İlk çağırma Notepad başlatır.</span><span class="sxs-lookup"><span data-stu-id="a5341-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="a5341-156">İkinci çağırma yerel makine üzerinde çalışan işlemlerin bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="a5341-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="a5341-157">`Output`değişkeni komutunun çıktısını depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5341-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="a5341-158">Sonraki çağrı, bir işlem sonrası adımı PowerShell çağırma tek tek her çıkışta çalıştırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5341-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="a5341-159">`InitializationAction`Her işlem için dize gösterimi çıkarır işlevi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a5341-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="a5341-160">Bu dizeler koleksiyonu döndürülür `Output` tarafından değişken `InvokePowerShell<string>` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="a5341-161">Başarılı `InvokePowerShell` çağrıları etkinlik ve çıkış ve hataları alma veri geçirme göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a5341-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="a5341-162">Tasarımcı istemci projesi kullanma</span><span class="sxs-lookup"><span data-stu-id="a5341-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="a5341-163">Özel etkinlikler, neredeyse her biri yerleşik içeren bir dizi DesignerClient proje oluşur `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="a5341-164">Etkinliklerin çoğu çağrı genel olmayan sürümü `InvokePowerShell` etkinliği ve bir dönüş değeri beklemediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a5341-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="a5341-165">Diğer etkinlikler genel sürümünü kullanmanız `InvokePowerShell` etkinlik ve kullanım `InitializationAction` sonuçları sonrası işlemek için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="a5341-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="a5341-166">PowerShell projesine kullanma</span><span class="sxs-lookup"><span data-stu-id="a5341-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="a5341-167">Ana eylem etkinliğin gerçekleşir `ExecutePowerShell` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a5341-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="a5341-168">PowerShell komutlarının yürütülmesini ana iş akışı iş parçacığı uğramaması değil çünkü etkinlik devralarak zaman uyumsuz bir etkinlik olarak oluşturulan <xref:System.Activities.AsyncCodeActivity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a5341-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="a5341-169"><xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Yöntemi, etkinlik çalıştırmaya başlamak için iş akışı çalışma zamanı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a5341-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="a5341-170">PowerShell komut zinciri oluşturmak için PowerShell API'ları çağırarak başlar.</span><span class="sxs-lookup"><span data-stu-id="a5341-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="a5341-171">PowerShell komut oluşturur ve parametreler ve değişkenler ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="a5341-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="a5341-172">İçinde yöneltilen girişleri de bu noktada ardışık düzene gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a5341-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="a5341-173">Ardışık Düzen son olarak, paketlenir bir `PipelineInvokerAsyncResult` nesne ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a5341-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="a5341-174">`PipelineInvokerAsyncResult` Nesne dinleyicisi kaydeder ve ardışık düzen çağırır.</span><span class="sxs-lookup"><span data-stu-id="a5341-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="a5341-175">Yürütme tamamlandığında, çıkış ve hata aynı içinde depolanan `PipelineInvokerAsyncResult` nesne ve denetim karmalayan geri için iş akışı çalışma zamanı için başlangıçta kendisine geçirilen geri çağırma yöntemini çağırarak <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5341-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="a5341-176">Yöntemin yürütme sonunda, iş akışı çalışma zamanı etkinliğin çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a5341-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="a5341-177">`InvokePowerShell` Sınıf sarmalayan `ExecutePowerShellCommand` sınıf ve etkinlik; genel bir sürümü iki sürümü ve genel olmayan sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5341-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="a5341-178">Genel tür bağımsız sonuçları genel sürüm dönüştürür ancak genel olmayan sürümü PowerShell yürütme çıktısı, doğrudan döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5341-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="a5341-179">Etkinlik genel sürümünü çağıran sıralı iş akışı olarak uygulanan `ExecutePowerShellCommand` ve sonuçlarını sonrası işler.</span><span class="sxs-lookup"><span data-stu-id="a5341-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="a5341-180">Sonuç koleksiyondaki her öğe için işlem sonrası adımı çağırır `InitializationAction` Bu ayarlanırsa.</span><span class="sxs-lookup"><span data-stu-id="a5341-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="a5341-181">Aksi takdirde, basit bir cast yapar.</span><span class="sxs-lookup"><span data-stu-id="a5341-181">Otherwise, it does a simple cast.</span></span>  
  
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
  
 <span data-ttu-id="a5341-182">Her iki `InvokePowerShell` etkinlikleri (genel ve genel olmayan), bir tasarımcı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="a5341-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="a5341-183">InvokePowerShellDesigner.xaml ve onun ilişkili .cs dosyası tanımlayın görünümünü [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] genel olmayan sürümü için `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="a5341-184">InvokePowerShellDesigner.xaml içinde bir <xref:System.Windows.Controls.DockPanel> grafik arabirim temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5341-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="a5341-185">Unutmayın `Text` özelliktir metin kutusunun etkinliğin değerini sağlar iki yönlü bir bağlama `CommandText` özelliği, Tasarımcı değeri giriş eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a5341-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="a5341-186">GenericInvokePowerShellDesigner.xaml ve onun ilişkili .cs dosyası tanımlayın genel için grafik arabirimine `InvokePowerShell` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a5341-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="a5341-187">Ayarlamak kullanıcılara izin verdiği için tasarımcı biraz daha karmaşıktır bir `InitializationAction`.</span><span class="sxs-lookup"><span data-stu-id="a5341-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="a5341-188">Kullanımını anahtar öğedir <xref:System.Activities.Presentation.WorkflowItemPresenter> sürükleme izin vermek ve bırakma alt etkinliklerin `InvokePowerShell` Tasarımcı yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="a5341-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="a5341-189">Tasarımcı özelleştirme tasarım tuvalde etkinlik görünümünü tanımlamak .xaml dosyalarla durdurmaz.</span><span class="sxs-lookup"><span data-stu-id="a5341-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="a5341-190">Etkinlik parametreleri görüntülemek için kullanılan iletişim kutuları da özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a5341-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="a5341-191">Bu parametreler ve PowerShell değişkenleri PowerShell komutlarını davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="a5341-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="a5341-192">Etkinlik olarak kullanıma sunar <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` türleri.</span><span class="sxs-lookup"><span data-stu-id="a5341-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="a5341-193">Bu tür düzenlemenizi sağlar iletişim kutusu ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml ve PropertyEditorResources.cs tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a5341-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a5341-194">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a5341-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="a5341-195">Bu örneği çalıştırmak için Windows PowerShell yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5341-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="a5341-196">Windows PowerShell Bu konumdan yüklenebilir: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span><span class="sxs-lookup"><span data-stu-id="a5341-196">Windows PowerShell can be installed from this location: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="a5341-197">Kodlanmış istemci çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a5341-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="a5341-198">Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5341-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5341-199">Çözüme sağ tıklayın ve bunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5341-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="a5341-200">Sağ **CodedClient** proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="a5341-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="a5341-201">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a5341-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="a5341-202">Tasarımcı istemci çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a5341-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="a5341-203">Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5341-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5341-204">Çözüme sağ tıklayın ve bunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5341-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="a5341-205">Sağ **DesignerClient** proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="a5341-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="a5341-206">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a5341-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="a5341-207">Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="a5341-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="a5341-208">Başvuran varsa `InvokePowerShell` etkinlik derleme veya proje derleme hatası sonuçlarında başka bir projeden, ihtiyacınız olabilecek el ile eklemek `<SpecificVersion>True</SpecificVersion>` .csproj dosyasına başvuruda bulunan satırı altında yeni proje öğesi `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="a5341-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="a5341-209">Windows PowerShell yüklü değil, eklediğiniz hemen Visual Studio aşağıdaki hata iletisi görüntülenir bir `InvokePowerShell` etkinliğini bir iş akışı üzerine:`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="a5341-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="a5341-210">Windows PowerShell 2. 0 ', program aracılığıyla arama `$input.MoveNext()` başarısız olur ve kullanan komut dosyaları `$input.MoveNext()` istenmeyen hataları ve sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="a5341-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="a5341-211">Bu sorunu çözmek için PowerShell fiil kullanmayı düşünün `foreach` çağırmak yerine `MoveNext()` bir dizi dolaşırken.</span><span class="sxs-lookup"><span data-stu-id="a5341-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5341-212">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a5341-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5341-213">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a5341-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a5341-214">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a5341-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5341-215">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a5341-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="see-also"></a><span data-ttu-id="a5341-216">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5341-216">See Also</span></span>
