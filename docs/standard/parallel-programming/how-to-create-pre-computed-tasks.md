---
title: "Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma"
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
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="b4812-102">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4812-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="b4812-103">Bu belge nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> önbellekte tutulur zaman uyumsuz indirme işlemlerinin sonuçlarını alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b4812-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="b4812-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Yöntem bir tamamlanmış <xref:System.Threading.Tasks.Task%601> olarak sağlanan değer tutan nesnenin kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b4812-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="b4812-105">Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="b4812-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4812-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4812-106">Example</span></span>  
 <span data-ttu-id="b4812-107">Aşağıdaki örnek dizeleri Web'den indirir.</span><span class="sxs-lookup"><span data-stu-id="b4812-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="b4812-108">Tanımladığı `DownloadStringAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b4812-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="b4812-109">Bu yöntem dizeleri web üzerinden zaman uyumsuz olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="b4812-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="b4812-110">Bu örnek ayrıca kullanan bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerinin sonuçlarını önbelleğe almak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b4812-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="b4812-111">Bu önbellek, giriş adresi tutulursa `DownloadStringAsync` kullanır <xref:System.Threading.Tasks.Task.FromResult%2A> üretmek için yöntemi bir <xref:System.Threading.Tasks.Task%601> bu adresinde içeriğini tutan nesne.</span><span class="sxs-lookup"><span data-stu-id="b4812-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="b4812-112">Aksi takdirde `DownloadStringAsync` web sunucusundan dosya indirir ve önbelleğe sonuç ekler.</span><span class="sxs-lookup"><span data-stu-id="b4812-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="b4812-113">Bu örnekte, iki kez birden çok dizenin indirmek için gereken süreyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="b4812-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="b4812-114">Sonuçları önbellekte tutulur çünkü indirme işlemleri ikinci kümesi ilk kümesi'den daha az zaman almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4812-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="b4812-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi etkinleştirir `DownloadStringAsync` oluşturmak için yöntemi <xref:System.Threading.Tasks.Task%601> bunlar tutun nesneleri önceden hesaplanan sonuçları.</span><span class="sxs-lookup"><span data-stu-id="b4812-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4812-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b4812-116">Compiling the Code</span></span>  
 <span data-ttu-id="b4812-117">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `CachedDownloads.cs` (`CachedDownloads.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b4812-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="b4812-118">**csc.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="b4812-118">**csc.exe CachedDownloads.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="b4812-119">**Vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="b4812-119">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b4812-120">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b4812-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4812-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4812-121">See Also</span></span>  
 [<span data-ttu-id="b4812-122">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="b4812-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
