---
title: 'Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123133"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="fe5da-102">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe5da-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="fe5da-103">Bu belgede, bir önbellekte tutulan zaman uyumsuz indirme işlemlerinin sonuçlarını almak için <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> yönteminin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe5da-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="fe5da-104"><xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği olarak belirtilen değeri tutan bir tamamlanmış <xref:System.Threading.Tasks.Task%601> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe5da-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="fe5da-105">Bu yöntem, bir <xref:System.Threading.Tasks.Task%601> nesnesi döndüren zaman uyumsuz bir işlem gerçekleştirirken ve bu <xref:System.Threading.Tasks.Task%601> nesnesinin sonucu zaten hesaplanmışsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="fe5da-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe5da-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe5da-106">Example</span></span>  
 <span data-ttu-id="fe5da-107">Aşağıdaki örnek dizeleri Web 'den indirir.</span><span class="sxs-lookup"><span data-stu-id="fe5da-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="fe5da-108">`DownloadStringAsync` yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe5da-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="fe5da-109">Bu yöntem, dizeleri zaman uyumsuz olarak Web 'den indirir.</span><span class="sxs-lookup"><span data-stu-id="fe5da-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="fe5da-110">Bu örnek, önceki işlemlerin sonuçlarını önbelleğe almak için de bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe5da-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="fe5da-111">Giriş adresi bu önbellekte tutuluyorsa `DownloadStringAsync`, bu adresteki içeriği tutan bir <xref:System.Threading.Tasks.Task%601> nesnesi oluşturmak için <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe5da-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="fe5da-112">Aksi takdirde, `DownloadStringAsync` dosyayı Web 'den indirir ve sonucu önbelleğe ekler.</span><span class="sxs-lookup"><span data-stu-id="fe5da-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="fe5da-113">Bu örnek, birden çok dizeyi iki kez indirmek için gereken zamanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="fe5da-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="fe5da-114">İkinci indirme işlemleri kümesi, sonuçlar önbellekte tutulduğundan ilk ayarlanan süreden daha az zaman almalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe5da-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="fe5da-115"><xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi, `DownloadStringAsync` yönteminin önceden hesaplanan bu sonuçları tutan <xref:System.Threading.Tasks.Task%601> nesneleri oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe5da-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5da-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe5da-116">See also</span></span>

- [<span data-ttu-id="fe5da-117">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="fe5da-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
