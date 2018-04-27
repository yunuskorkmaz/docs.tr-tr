---
title: 'Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e47355ceebaa00a8a688dc56bfd9e647da79ded2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="e5296-102">Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="e5296-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="e5296-103">Bu belge TPL veri akışı kitaplığı üretici-tüketici düzeni uygulama için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5296-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="e5296-104">Bu modelde *üretici* ileti bloğu iletileri gönderir ve *tüketici* bu bloğundan iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="e5296-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a><span data-ttu-id="e5296-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5296-105">Example</span></span>  
 <span data-ttu-id="e5296-106">Aşağıdaki örnek, veri akışı kullanan bir temel üretici-tüketici modeli gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5296-106">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="e5296-107">`Produce` Yöntemi Yazar rastgele bayt veri içeren diziler bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesne ve `Consume` yöntemi okur bayt, kaynağı bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e5296-107">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="e5296-108">Üzerinde davranarak <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> ve <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> kendi türetilmiş türler yerine arabirimleri çeşitli veri akışı bloğu türlerini davranamaz yeniden kullanılabilir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5296-108">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="e5296-109">Bu örnekte <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5296-109">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="e5296-110">Çünkü <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> hem bir kaynak sınıfı görür engelleme ve hedef blok üretici ve tüketici paylaşılan bir nesnenin veri aktarmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5296-110">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="e5296-111">`Produce` Yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> zaman uyumlu olarak hedef blok veri yazmak için bir döngü yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5296-111">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="e5296-112">Sonra `Produce` yöntemi Yazar tüm verilerin hedef bloğuna çağırır <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> blok hiçbir zaman ek veriler kullanılabilir olduğunu belirtmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="e5296-112">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="e5296-113">`Consume` Yöntemi kullanan [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [bekleme](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic'te) için zaman uyumsuz olarak Toplam alınan bayt sayısı işlem <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="e5296-113">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="e5296-114">Zaman uyumsuz olarak davranacak şekilde `Consume` yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak blok verileri kullanılabilir ve kaynak blok hiçbir zaman ek veriler kullanılabilir olduğunda olduğunda bir bildirim almak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="e5296-114">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5296-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e5296-115">Compiling the Code</span></span>  
 <span data-ttu-id="e5296-116">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` Visual Basic), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5296-116">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="e5296-117">Visual C#</span><span class="sxs-lookup"><span data-stu-id="e5296-117">Visual C#</span></span>  
  
 <span data-ttu-id="e5296-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="e5296-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 <span data-ttu-id="e5296-119">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5296-119">Visual Basic</span></span>  
  
 <span data-ttu-id="e5296-120">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="e5296-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e5296-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e5296-121">Robust Programming</span></span>  
 <span data-ttu-id="e5296-122">Bu örnek yalnızca tek bir tüketici kaynak verileri işlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5296-122">This example uses just one consumer to process the source data.</span></span> <span data-ttu-id="e5296-123">Birden çok tüketiciye uygulamanızda varsa, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemi aşağıdaki örnekte gösterildiği gibi kaynak bloğundan veri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="e5296-123">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="e5296-124"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntemi döndürür `False` hiçbir veri olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5296-124">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="e5296-125">Birden çok tüketiciye eşzamanlı olarak kaynak blok erişmesi gerektiğinde bu mekanizma veri çağrısından sonra hala kullanılabilir olduğunu garanti <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5296-125">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5296-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5296-126">See Also</span></span>  
 [<span data-ttu-id="e5296-127">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="e5296-127">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
