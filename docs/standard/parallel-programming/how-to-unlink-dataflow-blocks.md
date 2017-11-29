---
title: "Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma"
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="9eb8d-102">Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma</span><span class="sxs-lookup"><span data-stu-id="9eb8d-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="9eb8d-103">Bu belge, bir hedef veri akışı blok kaynağından bağlantısının nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-103">This document describes how to unlink a target dataflow block from its source.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="9eb8d-104">TPL veri akışı kitaplığı (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9eb8d-104">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="9eb8d-105">Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-105">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb8d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9eb8d-106">Example</span></span>  
 <span data-ttu-id="9eb8d-107">Aşağıdaki örnek, üç oluşturur <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneleri, her hangi çağrılarının `TrySolution` bir değeri hesaplamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-107">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="9eb8d-108">Bu örnek, yalnızca ilk çağrıda sonucundan gerektirir `TrySolution` tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-108">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="9eb8d-109">İlk değer almasını <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> bittikten nesnesi, bu örnek tanımlar `ReceiveFromAny(T)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-109">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="9eb8d-110">`ReceiveFromAny(T)` Yöntemi kabul eden bir dizi <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneleri ve bu nesnelerin her biri bağlantılar bir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-110">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="9eb8d-111">Kullandığınızda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi bir kaynak veri akışı bloğu kaynak, bir hedef blok bağlamak için veri olarak kullanılabilir hale geldiğinde hedef iletileri yayar.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-111">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="9eb8d-112">Çünkü <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> sınıfı sunulur, ilk iletiyi kabul `ReceiveFromAny(T)` yöntemi çağrılarak sonucu üretir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-112">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="9eb8d-113">Bu için sunulan ilk ileti oluşturur <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-113">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="9eb8d-114"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi alır aşırı yüklenmiş bir sürümü olan bir <xref:System.Boolean> parametresi `unlinkAfterOne` , onu ayarlandığında `True`, hedef kaynak sunucudan bir iletiyi aldıktan sonra hedef bağlantısını kesmek için kaynak blok bildirir.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-114">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="9eb8d-115">Önemlidir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> çünkü kendi kaynaklardan bağlantısını nesnesine kaynakları dizisi arasındaki ilişkiyi ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne sonra gerekli artık <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesini bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-115">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="9eb8d-116">Kalan çağrılar etkinleştirmek için `TrySolution` bunlardan birini bir değeri hesaplar sonra sona erdirmek için `TrySolution` metodu bir <xref:System.Threading.CancellationToken> çağrısından sonra iptal nesne `ReceiveFromAny(T)` döndürür.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-116">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="9eb8d-117"><xref:System.Threading.SpinWait.SpinUntil%2A> Yöntemi döndürür bu <xref:System.Threading.CancellationToken> nesnesi iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-117">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9eb8d-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9eb8d-118">Compiling the Code</span></span>  
 <span data-ttu-id="9eb8d-119">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-119">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="9eb8d-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="9eb8d-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="9eb8d-121">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="9eb8d-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9eb8d-122">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9eb8d-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb8d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9eb8d-123">See Also</span></span>  
 [<span data-ttu-id="9eb8d-124">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="9eb8d-124">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
