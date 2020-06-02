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
ms.openlocfilehash: 88f0782380d21858bc5dd0fc0fbf63bbf85403b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289999"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="3592f-102">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3592f-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="3592f-103">Bu belgede, <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> bir önbellekte tutulan zaman uyumsuz indirme işlemlerinin sonuçlarını almak için yönteminin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3592f-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="3592f-104"><xref:System.Threading.Tasks.Task.FromResult%2A>Yöntemi, <xref:System.Threading.Tasks.Task%601> özelliği olarak belirtilen değeri tutan tamamlanmış bir nesne döndürür <xref:System.Threading.Tasks.Task%601.Result%2A> .</span><span class="sxs-lookup"><span data-stu-id="3592f-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="3592f-105">Bu yöntem, bir nesne döndüren zaman uyumsuz bir işlem gerçekleştirirken ve bu <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task%601> nesnenin sonucu zaten hesaplanmışsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3592f-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3592f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3592f-106">Example</span></span>  
 <span data-ttu-id="3592f-107">Aşağıdaki örnek dizeleri Web 'den indirir.</span><span class="sxs-lookup"><span data-stu-id="3592f-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="3592f-108">`DownloadStringAsync`Yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3592f-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="3592f-109">Bu yöntem, dizeleri zaman uyumsuz olarak Web 'den indirir.</span><span class="sxs-lookup"><span data-stu-id="3592f-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="3592f-110">Bu örnek <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , önceki işlemlerin sonuçlarını önbelleğe almak için de bir nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3592f-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="3592f-111">Giriş adresi bu önbellekte tutuluyorsa, bu `DownloadStringAsync` <xref:System.Threading.Tasks.Task.FromResult%2A> adresteki içeriği tutan bir nesne oluşturmak için yöntemini kullanır <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="3592f-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="3592f-112">Aksi takdirde, `DownloadStringAsync` dosyayı Web 'den indirir ve sonucu önbelleğe ekler.</span><span class="sxs-lookup"><span data-stu-id="3592f-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="3592f-113">Bu örnek, birden çok dizeyi iki kez indirmek için gereken zamanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3592f-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="3592f-114">İkinci indirme işlemleri kümesi, sonuçlar önbellekte tutulduğundan ilk ayarlanan süreden daha az zaman almalıdır.</span><span class="sxs-lookup"><span data-stu-id="3592f-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="3592f-115"><xref:System.Threading.Tasks.Task.FromResult%2A>Yöntemi, `DownloadStringAsync` yönteminin <xref:System.Threading.Tasks.Task%601> Bu önceden hesaplanan sonuçları tutan nesneler oluşturmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3592f-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3592f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3592f-116">See also</span></span>

- [<span data-ttu-id="3592f-117">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="3592f-117">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
