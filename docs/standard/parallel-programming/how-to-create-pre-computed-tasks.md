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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123133"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="d071e-102">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d071e-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="d071e-103">Bu belge, önbellekte tutulan eşenkron indirme işlemlerinin sonuçlarını almak için <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> yöntemin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d071e-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="d071e-104">Yöntem, <xref:System.Threading.Tasks.Task.FromResult%2A> sağlanan <xref:System.Threading.Tasks.Task%601> değeri <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği olarak tutan bitmiş bir nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d071e-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="d071e-105">Bu yöntem, bir <xref:System.Threading.Tasks.Task%601> nesne döndüren bir eşyoklama işlemi gerçekleştirdiğinizde <xref:System.Threading.Tasks.Task%601> ve bu nesnenin sonucu zaten hesaplandığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d071e-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d071e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d071e-106">Example</span></span>  
 <span data-ttu-id="d071e-107">Aşağıdaki örnek, dizeleri web'den indirir.</span><span class="sxs-lookup"><span data-stu-id="d071e-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="d071e-108">`DownloadStringAsync` Yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d071e-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="d071e-109">Bu yöntem, dizeleri web'den eşzamanlı olarak indirir.</span><span class="sxs-lookup"><span data-stu-id="d071e-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="d071e-110">Bu örnek, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerin sonuçlarını önbelleğe almak için bir nesne de kullanır.</span><span class="sxs-lookup"><span data-stu-id="d071e-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="d071e-111">Giriş adresi bu önbellekte `DownloadStringAsync` tutulursa, <xref:System.Threading.Tasks.Task.FromResult%2A> içeriği bu <xref:System.Threading.Tasks.Task%601> adreste tutan bir nesne oluşturmak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d071e-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="d071e-112">Aksi `DownloadStringAsync` takdirde, dosyayı web'den indirir ve sonucu önbelleğe ekler.</span><span class="sxs-lookup"><span data-stu-id="d071e-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="d071e-113">Bu örnek, birden çok dizeleri iki kez indirmek için gereken süreyi hesaplamak.</span><span class="sxs-lookup"><span data-stu-id="d071e-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="d071e-114">Sonuçlar önbellekte tutulduğundan, ikinci indirme işlemleri kümesi ilk kümeden daha az zaman almalıdır.</span><span class="sxs-lookup"><span data-stu-id="d071e-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="d071e-115">Yöntem, <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemin `DownloadStringAsync` bu <xref:System.Threading.Tasks.Task%601> önceden hesaplanmış sonuçları tutan nesneler oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d071e-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d071e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d071e-116">See also</span></span>

- [<span data-ttu-id="d071e-117">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="d071e-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
