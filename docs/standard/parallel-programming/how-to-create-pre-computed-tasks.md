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
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 262aa626e9e426da94de0d2ad5f2ef04a5bbc5f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="2c137-102">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c137-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="2c137-103">Bu belge nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> önbellekte tutulur zaman uyumsuz indirme işlemlerinin sonuçlarını alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2c137-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="2c137-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Yöntem bir tamamlanmış <xref:System.Threading.Tasks.Task%601> olarak sağlanan değer tutan nesnenin kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2c137-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="2c137-105">Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2c137-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c137-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c137-106">Example</span></span>  
 <span data-ttu-id="2c137-107">Aşağıdaki örnek dizeleri Web'den indirir.</span><span class="sxs-lookup"><span data-stu-id="2c137-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="2c137-108">Tanımladığı `DownloadStringAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2c137-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="2c137-109">Bu yöntem dizeleri web üzerinden zaman uyumsuz olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="2c137-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="2c137-110">Bu örnek ayrıca kullanan bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerinin sonuçlarını önbelleğe almak için nesne.</span><span class="sxs-lookup"><span data-stu-id="2c137-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="2c137-111">Bu önbellek, giriş adresi tutulursa `DownloadStringAsync` kullanır <xref:System.Threading.Tasks.Task.FromResult%2A> üretmek için yöntemi bir <xref:System.Threading.Tasks.Task%601> bu adresinde içeriğini tutan nesne.</span><span class="sxs-lookup"><span data-stu-id="2c137-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="2c137-112">Aksi takdirde `DownloadStringAsync` web sunucusundan dosya indirir ve önbelleğe sonuç ekler.</span><span class="sxs-lookup"><span data-stu-id="2c137-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="2c137-113">Bu örnekte, iki kez birden çok dizenin indirmek için gereken süreyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2c137-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="2c137-114">Sonuçları önbellekte tutulur çünkü indirme işlemleri ikinci kümesi ilk kümesi'den daha az zaman almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c137-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="2c137-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi etkinleştirir `DownloadStringAsync` oluşturmak için yöntemi <xref:System.Threading.Tasks.Task%601> bunlar tutun nesneleri önceden hesaplanan sonuçları.</span><span class="sxs-lookup"><span data-stu-id="2c137-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2c137-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2c137-116">Compiling the Code</span></span>  
 <span data-ttu-id="2c137-117">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `CachedDownloads.cs` (`CachedDownloads.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2c137-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="2c137-118">**csc.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="2c137-118">**csc.exe CachedDownloads.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="2c137-119">**Vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="2c137-119">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2c137-120">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2c137-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c137-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c137-121">See Also</span></span>  
 [<span data-ttu-id="2c137-122">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="2c137-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
