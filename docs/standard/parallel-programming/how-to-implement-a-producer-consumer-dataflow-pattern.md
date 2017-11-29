---
title: "Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="51ab5-102">Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="51ab5-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="51ab5-103">Bu belge TPL veri akışı kitaplığı üretici-tüketici düzeni uygulama için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="51ab5-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="51ab5-104">Bu modelde *üretici* ileti bloğu iletileri gönderir ve *tüketici* bu bloğundan iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="51ab5-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="51ab5-105">TPL veri akışı kitaplığı (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51ab5-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="51ab5-106">Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.</span><span class="sxs-lookup"><span data-stu-id="51ab5-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51ab5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="51ab5-107">Example</span></span>  
 <span data-ttu-id="51ab5-108">Aşağıdaki örnek, veri akışı kullanan bir temel üretici-tüketici modeli gösterir.</span><span class="sxs-lookup"><span data-stu-id="51ab5-108">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="51ab5-109">`Produce` Yöntemi Yazar rastgele bayt veri içeren diziler bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesne ve `Consume` yöntemi okur bayt, kaynağı bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="51ab5-109">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="51ab5-110">Üzerinde davranarak <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> ve <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> kendi türetilmiş türler yerine arabirimleri çeşitli veri akışı bloğu türlerini davranamaz yeniden kullanılabilir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51ab5-110">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="51ab5-111">Bu örnekte <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="51ab5-111">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="51ab5-112">Çünkü <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> hem bir kaynak sınıfı görür engelleme ve hedef blok üretici ve tüketici paylaşılan bir nesnenin veri aktarmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51ab5-112">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="51ab5-113">`Produce` Yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> zaman uyumlu olarak hedef blok veri yazmak için bir döngü yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51ab5-113">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="51ab5-114">Sonra `Produce` yöntemi Yazar tüm verilerin hedef bloğuna çağırır <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> blok hiçbir zaman ek veriler kullanılabilir olduğunu belirtmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="51ab5-114">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="51ab5-115">`Consume` Yöntemi kullanan [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [bekleme](~/docs/visual-basic/language-reference/operators/await-operator.md) içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) için Toplam alınan bayt sayısı zaman uyumsuz işlem <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="51ab5-115">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="51ab5-116">Zaman uyumsuz olarak davranacak şekilde `Consume` yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak blok verileri kullanılabilir ve kaynak blok hiçbir zaman ek veriler kullanılabilir olduğunda olduğunda bir bildirim almak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="51ab5-116">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51ab5-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="51ab5-117">Compiling the Code</span></span>  
 <span data-ttu-id="51ab5-118">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="51ab5-118">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="51ab5-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="51ab5-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="51ab5-120">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="51ab5-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="51ab5-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="51ab5-121">Robust Programming</span></span>  
 <span data-ttu-id="51ab5-122">Bu örnek yalnızca tek bir tüketici kaynak verileri işlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="51ab5-122">This example uses just one consumer to process the source data.</span></span> <span data-ttu-id="51ab5-123">Birden çok tüketiciye uygulamanızda varsa, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemi aşağıdaki örnekte gösterildiği gibi kaynak bloğundan veri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="51ab5-123">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="51ab5-124"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntemi döndürür `False` hiçbir veri olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51ab5-124">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="51ab5-125">Birden çok tüketiciye eşzamanlı olarak kaynak blok erişmesi gerektiğinde bu mekanizma veri çağrısından sonra hala kullanılabilir olduğunu garanti <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="51ab5-125">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ab5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51ab5-126">See Also</span></span>  
 [<span data-ttu-id="51ab5-127">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="51ab5-127">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
