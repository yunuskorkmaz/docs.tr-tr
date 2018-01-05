---
title: "NoPersistScope etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc651403988fa7558f79a4c99e42fb776efec4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="bbc27-102">NoPersistScope etkinliği</span><span class="sxs-lookup"><span data-stu-id="bbc27-102">NoPersistScope Activity</span></span>
<span data-ttu-id="bbc27-103">Bu örnek, bir iş akışındaki serileştirilebilir olmayan ve tek kullanımlık bir durumu işlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bbc27-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="bbc27-104">Seri hale getirilemeyen durumu devam ettirmek iş akışları çalışmayın ve ayrıca atılabilir nesnelerinin iş akışında kullanıldıktan sonra Temizlenen önemli olduğunu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bbc27-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bbc27-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="bbc27-105">Demonstrates</span></span>  
 <span data-ttu-id="bbc27-106">`NoPersistScope`Özel Etkinlik ve Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="bbc27-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="bbc27-107">NoPersistZone etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="bbc27-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="bbc27-108">Örnek iş akışı çalıştığında, özel bir aktivite olarak adlandırılan `CreateTextWriter` türünde bir nesne oluşturur <xref:System.IO.TextWriter> ve bir iş akışı değişkenine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bbc27-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="bbc27-109"><xref:System.IO.TextWriter>olan bir <xref:System.IDisposable> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bbc27-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="bbc27-110">Bu <xref:System.IO.TextWriter>, örnek çalıştığı, dizindeki ' out.txt' adlı bir dosyaya yazmak için yapılandırıldığı tarafından kullanılıyor bir <xref:System.Activities.Statements.WriteLine> etkinlik olarak yazdığınız içinde konsolunda herhangi bir metin görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="bbc27-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="bbc27-111">Echo mantığı içinde çalışan bir `NoPersistScope` iş akışı kalıcı olmasını önler (kodu hangi Ayrıca bu örnek bir parçası) etkinlik.</span><span class="sxs-lookup"><span data-stu-id="bbc27-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="bbc27-112">Yazarsanız `unload` konsolunda ana iş akışı örneği kalıcı dener ancak iş akışı içinde kaldığından bu işlem zaman aşımına uğradı bir `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="bbc27-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="bbc27-113">İş akışı da adlı özel bir aktivite kullanır `Dispose` silmek için <xref:System.IO.TextWriter> nesne iş akışı tamamlandığında kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="bbc27-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="bbc27-114">`Dispose` Etkinlik içinde yerleştirilir <xref:System.Activities.Statements.TryCatch.Finally%2A> , engellemek <xref:System.Activities.Statements.TryCatch> , etkinlik <xref:System.IO.TextWriter> değişkeni bildirilen, bir özel durum Try bloğunun yürütülmesi sırasında gerçekleşeceğini olsa bile bu çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="bbc27-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="bbc27-115">Yazabilirsiniz `exit` iş akışı örneği tamamlamak ve programdan çıkın.</span><span class="sxs-lookup"><span data-stu-id="bbc27-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="bbc27-116">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bbc27-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="bbc27-117">NoPersistZone.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbc27-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbc27-118">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="bbc27-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="bbc27-119">Derleme başarılı olduktan sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menü alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **Hata ayıklama** menü hata ayıklama olmadan çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="bbc27-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="bbc27-120">Temizleme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="bbc27-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="bbc27-121">SQL örneği deposuna kaldırmak için Cleanup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bbc27-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbc27-122">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbc27-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bbc27-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bbc27-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bbc27-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="bbc27-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bbc27-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bbc27-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`