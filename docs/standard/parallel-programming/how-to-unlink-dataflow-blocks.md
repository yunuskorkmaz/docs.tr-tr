---
title: 'Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: bc0f266169a2d82bb76355febd58b2268907fe97
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075689"
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="54211-102">Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma</span><span class="sxs-lookup"><span data-stu-id="54211-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="54211-103">Bu belge, bir hedef veri akışı bloğu kaynağından bağlantısının nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="54211-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="54211-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="54211-104">Example</span></span>  
 <span data-ttu-id="54211-105">Aşağıdaki örnek, üç oluşturur <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneler, her biri çağıran `TrySolution` bir değeri hesaplamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54211-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="54211-106">Bu örnek yalnızca ilk çağrıda sonuçtan gerektirir `TrySolution` tamamlanması.</span><span class="sxs-lookup"><span data-stu-id="54211-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="54211-107">İlk değeri almaya <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> biten nesne, bu örnek tanımlar `ReceiveFromAny(T)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54211-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="54211-108">`ReceiveFromAny(T)` Yöntemi, bir dizi kabul <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneler ve bağlantılar için bu nesnelerin her biri bir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="54211-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="54211-109">Kullanırken <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi bir kaynak veri akışı bloğunu hedef bloğa, kaynak bağlamak için veri kullanılabilir olduğunda hedef iletileri yayar.</span><span class="sxs-lookup"><span data-stu-id="54211-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="54211-110">Çünkü <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> sınıf sunulur, ilk iletiyi kabul `ReceiveFromAny(T)` yöntemi çağırarak sonucunu üreten <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54211-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="54211-111">Bu şekilde sunulan ilk ileti oluşturur <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="54211-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="54211-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi, alan bir aşırı yüklenmiş sürümüne sahip bir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> nesnesi ile bir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> özelliği, ayarlandığında `1`, hedef, kaynaktan bir ileti aldıktan sonra hedef bağlantısını kaldırmak için kaynak bloktaki bildirir .</span><span class="sxs-lookup"><span data-stu-id="54211-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes an <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> object with a <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> property that, when it is set to `1`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="54211-113">Önemlidir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> kaynaktan çünkü bağlantısını için nesne dizisi kaynakları arasındaki ilişkiyi ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne sonra gerekli artık <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="54211-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="54211-114">Kalan çağrılar için etkinleştirmek için `TrySolution` bunlardan biri bir değeri hesaplar sonra `TrySolution` yöntemi bir <xref:System.Threading.CancellationToken> çağrısından sonra iptal edilen bir nesne `ReceiveFromAny(T)` döndürür.</span><span class="sxs-lookup"><span data-stu-id="54211-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="54211-115"><xref:System.Threading.SpinWait.SpinUntil%2A> Yöntemi döndürür bu <xref:System.Threading.CancellationToken> nesnesi iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="54211-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54211-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="54211-116">Compiling the Code</span></span>  
 <span data-ttu-id="54211-117">Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` Visual Basic için), ve ardından bir Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="54211-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="54211-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="54211-118">Visual C#</span></span>  
  
 <span data-ttu-id="54211-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="54211-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 <span data-ttu-id="54211-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54211-120">Visual Basic</span></span>  
  
 <span data-ttu-id="54211-121">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="54211-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="54211-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54211-122">See also</span></span>

- [<span data-ttu-id="54211-123">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="54211-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
