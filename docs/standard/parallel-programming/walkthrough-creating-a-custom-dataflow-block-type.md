---
title: "İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 809b21fa6e1470890011604792d849998dd03ede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="0b7bc-102">İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b7bc-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="0b7bc-103">TPL veri akışı kitaplığı işlevleri, çeşitli etkinleştirmek birkaç veri akışı blok türü sağlasa da, özel blok türleri de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="0b7bc-104">Bu belge, özel davranışı uygulayan bir veri akışı blok türü oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b7bc-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0b7bc-105">Prerequisites</span></span>  
 <span data-ttu-id="0b7bc-106">Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) önce bu belgeyi okuyun.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-106">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you read this document.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="0b7bc-107">TPL veri akışı kitaplığı (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b7bc-107">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="0b7bc-108">Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-108">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="0b7bc-109">Kayan pencere veri akışı bloğu tanımlama</span><span class="sxs-lookup"><span data-stu-id="0b7bc-109">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="0b7bc-110">Giriş değerleri arabelleğe alınmış ve kayan bir pencere biçimde çıktı gerektiren bir veri akışı uygulaması göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-110">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="0b7bc-111">Örneğin, üç pencere boyutunu ve giriş değerler {0, 1, 2, 3, 4, 5} {0, 1, 2} çıkış dizileri kayan pencere veri akışı bloğu üretir {1, 2, 3}, {2, 3, 4} ve {3, 4, 5}.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-111">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="0b7bc-112">Aşağıdaki bölümlerde bu özel davranış uygulayan bir veri akışı blok türü oluşturmanın iki yolu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-112">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="0b7bc-113">İlk tekniği kullanan <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> işlevselliğini birleştirmek için yöntemi bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesne ve bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> bir yayılması bloğuna nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-113">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="0b7bc-114">İkinci tekniği türeyen bir sınıf tanımlar <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> ve özel davranış gerçekleştirmek için varolan birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-114">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="0b7bc-115">Kullanarak kayan pencere veri akışı bloğu tanımlamak için yöntemi yalıtma</span><span class="sxs-lookup"><span data-stu-id="0b7bc-115">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="0b7bc-116">Aşağıdaki örnek kullanır <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> yöntemi bir hedef ve kaynak yayılması bloğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-116">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="0b7bc-117">Bir kaynak bloğu ve bir alıcı ve veri göndereni görev yapması için hedef blok yayılması blok sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-117">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="0b7bc-118">Özel veri akışı işlevselliği gerektiren ancak ek yöntemler, özellikler veya alanlar sağlayan bir türü gerektirmeyen Bu teknik yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-118">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="0b7bc-119">Kayan pencere veri akışı bloğu tanımlamak için IPropagatorBlock türetme</span><span class="sxs-lookup"><span data-stu-id="0b7bc-119">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="0b7bc-120">Aşağıdaki örnekte gösterildiği `SlidingWindowBlock` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-120">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="0b7bc-121">Bu sınıfın türetildiği <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> böylece hem kaynak hem de veri hedefi olarak davranamaz.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-121">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="0b7bc-122">Önceki örnekte olduğu gibi `SlidingWindowBlock` sınıfı, var olan veri akışı bloğu türlerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-122">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="0b7bc-123">Ancak, `SlidingWindowBlock` sınıfı ayrıca gerekli olan yöntemleri uygulayan <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, ve <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-123">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="0b7bc-124">Bu yöntemler tüm İleri önceden tanımlanmış veri akışı blok türü üyelerine çalışır.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-124">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="0b7bc-125">Örneğin, `Post` yöntemi erteler iş `m_target` de veri üyesi bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-125">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="0b7bc-126">Özel veri akışı işlevselliği gerektirir ve ayrıca ek yöntemler, özellikler veya alanlar sağlayan bir türü gerektiren bu teknik yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-126">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="0b7bc-127">Örneğin, `SlidingWindowBlock` sınıfı ayrıca türetilen <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> böylece bunu sağlayabilir <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ve <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-127">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="0b7bc-128">`SlidingWindowBlock` Sınıfı ayrıca sağlayarak genişletilebilirlik gösterir `WindowSize` özelliği kayan pencere öğelerinde sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-128">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="0b7bc-129">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="0b7bc-129">The Complete Example</span></span>  
 <span data-ttu-id="0b7bc-130">Aşağıdaki örnek, bu kılavuz tam kod gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-130">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="0b7bc-131">Ayrıca, her iki kayan pencere blokları bloğuna yazar, ondan okuyan ve sonuçlarını konsola yazdırır bir yöntem kullanmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-131">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b7bc-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0b7bc-132">Compiling the Code</span></span>  
 <span data-ttu-id="0b7bc-133">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ve Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-133">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="0b7bc-134">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span><span class="sxs-lookup"><span data-stu-id="0b7bc-134">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="0b7bc-135">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span><span class="sxs-lookup"><span data-stu-id="0b7bc-135">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0b7bc-136">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0b7bc-136">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b7bc-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b7bc-137">See Also</span></span>  
 [<span data-ttu-id="0b7bc-138">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="0b7bc-138">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
