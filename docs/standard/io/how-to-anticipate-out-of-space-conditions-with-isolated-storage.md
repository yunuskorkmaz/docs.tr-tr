---
title: 'Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16b12a1ab274a63b8d190278d6312d36a61efe16
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649392"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="e56c3-102">Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme</span><span class="sxs-lookup"><span data-stu-id="e56c3-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>
<span data-ttu-id="e56c3-103">Yalıtılmış depolama kullanan kodu je omezeno tarafından bir [kota](../../../docs/standard/io/isolated-storage.md#quotas) veri bölümünde yalıtılmış depolama dosyalarının ve dizinleri mevcut en büyük boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e56c3-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="e56c3-104">Kota güvenlik ilkesi tarafından tanımlanır ve yöneticiler tarafından yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e56c3-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="e56c3-105">Veri yazma çalıştığınızda boyutu aşıldı izin verilen en fazla, bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum oluştu ve işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e56c3-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="e56c3-106">Bu uygulama, veri depolama alanı dolu olduğundan istekleri reddetmek neden olabilecek kötü amaçlı hizmet reddi saldırılarını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e56c3-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>  
  
 <span data-ttu-id="e56c3-107">Belirtilen yazma girişimi, bu nedenle, başarısız olma olasılığı yüksek olup olmadığını belirlemenize yardımcı olmak üzere <xref:System.IO.IsolatedStorage.IsolatedStorage> sınıfı üç salt okunur özellikler sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, ve <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="e56c3-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="e56c3-108">Bu özellikler, deposuna yazma olması deposunun boyutu izin verilen maksimum neden olup olmadığını belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e56c3-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="e56c3-109">Yalıtılmış Depolama etkilenebileceğini eşzamanlı olarak erişilebilir; Bu nedenle, kalan depolama miktarını işlem, depolama alanını bir depoya yazmak için deneyin zamanına göre tüketilebilecek.</span><span class="sxs-lookup"><span data-stu-id="e56c3-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="e56c3-110">Ancak, deponun en büyük boyutu kullanılabilir depolama alanı üst sınırına ulaşılmak üzere olup olmadığını belirlemenize yardımcı olması için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e56c3-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>  
  
 <span data-ttu-id="e56c3-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Özelliği düzgün şekilde çalışması için derlemeden kanıt bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e56c3-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="e56c3-112">Bu nedenle, bu özellik yalnızca almalıdır <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kullanılarak oluşturulan nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e56c3-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="e56c3-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> diğer herhangi bir yolla oluşturulan nesneleri (örneğin, öğesinden döndürülen nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi) doğru bir maksimum boyut döndürmez.</span><span class="sxs-lookup"><span data-stu-id="e56c3-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56c3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e56c3-114">Example</span></span>  
 <span data-ttu-id="e56c3-115">Aşağıdaki kod örneği bir yalıtılmış depolama alır, birkaç dosya oluşturur ve alır <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e56c3-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="e56c3-116">Kalan alanı bayt olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="e56c3-116">The remaining space is reported in bytes.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="e56c3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e56c3-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [<span data-ttu-id="e56c3-118">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="e56c3-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
- [<span data-ttu-id="e56c3-119">Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma</span><span class="sxs-lookup"><span data-stu-id="e56c3-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
