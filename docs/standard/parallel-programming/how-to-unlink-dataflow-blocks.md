---
title: 'Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c7cdfa227e330a4b8ed46395c9793e5dca570fac
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="2a482-102">Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2a482-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="2a482-103">Bu belge, bir hedef veri akışı blok kaynağından bağlantısının nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2a482-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="2a482-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a482-104">Example</span></span>  
 <span data-ttu-id="2a482-105">Aşağıdaki örnek, üç oluşturur <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneleri, her hangi çağrılarının `TrySolution` bir değeri hesaplamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="2a482-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="2a482-106">Bu örnek, yalnızca ilk çağrıda sonucundan gerektirir `TrySolution` tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="2a482-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="2a482-107">İlk değer almasını <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> bittikten nesnesi, bu örnek tanımlar `ReceiveFromAny(T)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2a482-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="2a482-108">`ReceiveFromAny(T)` Yöntemi kabul eden bir dizi <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneleri ve bu nesnelerin her biri bağlantılar bir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2a482-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="2a482-109">Kullandığınızda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi bir kaynak veri akışı bloğu kaynak, bir hedef blok bağlamak için veri olarak kullanılabilir hale geldiğinde hedef iletileri yayar.</span><span class="sxs-lookup"><span data-stu-id="2a482-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="2a482-110">Çünkü <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> sınıfı sunulur, ilk iletiyi kabul `ReceiveFromAny(T)` yöntemi çağrılarak sonucu üretir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2a482-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="2a482-111">Bu için sunulan ilk ileti oluşturur <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2a482-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="2a482-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi alır aşırı yüklenmiş bir sürümü olan bir <xref:System.Boolean> parametresi `unlinkAfterOne` , onu ayarlandığında `True`, hedef kaynak sunucudan bir iletiyi aldıktan sonra hedef bağlantısını kesmek için kaynak blok bildirir.</span><span class="sxs-lookup"><span data-stu-id="2a482-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="2a482-113">Önemlidir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> çünkü kendi kaynaklardan bağlantısını nesnesine kaynakları dizisi arasındaki ilişkiyi ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne sonra gerekli artık <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesini bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="2a482-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="2a482-114">Kalan çağrılar etkinleştirmek için `TrySolution` bunlardan birini bir değeri hesaplar sonra sona erdirmek için `TrySolution` metodu bir <xref:System.Threading.CancellationToken> çağrısından sonra iptal nesne `ReceiveFromAny(T)` döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a482-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="2a482-115"><xref:System.Threading.SpinWait.SpinUntil%2A> Yöntemi döndürür bu <xref:System.Threading.CancellationToken> nesnesi iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="2a482-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a482-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2a482-116">Compiling the Code</span></span>  
 <span data-ttu-id="2a482-117">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` Visual Basic), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2a482-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="2a482-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="2a482-118">Visual C#</span></span>  
  
 <span data-ttu-id="2a482-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="2a482-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 <span data-ttu-id="2a482-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a482-120">Visual Basic</span></span>  
  
 <span data-ttu-id="2a482-121">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="2a482-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="2a482-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a482-122">See Also</span></span>  
 [<span data-ttu-id="2a482-123">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="2a482-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
