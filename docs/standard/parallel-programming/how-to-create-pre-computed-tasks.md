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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e68465b6fae39089600457414e7f2a2328f725b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593129"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="d2bea-102">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2bea-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="d2bea-103">Bu belgenin nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> zaman uyumsuz indirme işlemlerinin bir ön bellekte tutulan sonuçlarını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2bea-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="d2bea-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi döndürür bir tamamlanmış <xref:System.Threading.Tasks.Task%601> olarak sağlanan değeri tutan bir nesne kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d2bea-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="d2bea-105">Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanmışsa.</span><span class="sxs-lookup"><span data-stu-id="d2bea-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2bea-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2bea-106">Example</span></span>  
 <span data-ttu-id="d2bea-107">Aşağıdaki örnek, dizeleri Web'den indirir.</span><span class="sxs-lookup"><span data-stu-id="d2bea-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="d2bea-108">Tanımladığı `DownloadStringAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2bea-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="d2bea-109">Bu yöntem, dizeleri zaman uyumsuz olarak Web'den indirir.</span><span class="sxs-lookup"><span data-stu-id="d2bea-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="d2bea-110">Bu örnekte ayrıca bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerinin sonuçlarını önbelleğe almak için nesne.</span><span class="sxs-lookup"><span data-stu-id="d2bea-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="d2bea-111">Giriş adresi bu önbellekte tutulan varsa `DownloadStringAsync` kullanan <xref:System.Threading.Tasks.Task.FromResult%2A> üretmek için yöntemi bir <xref:System.Threading.Tasks.Task%601> adreste içeriğini tutan nesne.</span><span class="sxs-lookup"><span data-stu-id="d2bea-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="d2bea-112">Aksi takdirde, `DownloadStringAsync` dosyayı Web'den indirir ve önbelleğe sonucu ekler.</span><span class="sxs-lookup"><span data-stu-id="d2bea-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="d2bea-113">Bu örnek, birden çok dizeyi iki kez indirmek için gereken süreyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d2bea-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="d2bea-114">Sonuçları önbellekte tutulan olduğundan ikinci indirme işlemlerinin kümesini ilk süreden daha kısa zamanda almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2bea-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="d2bea-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi etkinleştirir `DownloadStringAsync` yöntemini <xref:System.Threading.Tasks.Task%601> bu tutun nesneleri önceden hesaplanan sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="d2bea-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2bea-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2bea-116">See also</span></span>

- [<span data-ttu-id="d2bea-117">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="d2bea-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
