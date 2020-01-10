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
- quantity of isolated storage used
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
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708121"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="036a5-102">Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme</span><span class="sxs-lookup"><span data-stu-id="036a5-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="036a5-103">Yalıtılmış depolama kullanan kod, yalıtılmış depolama dosyalarının ve dizinlerinin mevcut olduğu veri bölmesi için en büyük boyutu belirten bir [Kota](../../../docs/standard/io/isolated-storage.md#quotas) ile kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="036a5-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="036a5-104">Kota güvenlik ilkesi tarafından tanımlanır ve yöneticiler tarafından yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="036a5-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="036a5-105">Veri yazmaya çalıştığınızda izin verilen en büyük boyut aşılırsa, <xref:System.IO.IsolatedStorage.IsolatedStorageException> bir özel durum oluşturulur ve işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="036a5-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="036a5-106">Bu, veri depolama alanı doldurulduğundan uygulamanın istekleri reddetmesine neden olabilecek kötü amaçlı hizmet reddi saldırılarını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="036a5-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="036a5-107">Bu nedenle, belirli bir yazma denemesinin başarısız olup olmadığını belirlemenize yardımcı olmak için <xref:System.IO.IsolatedStorage.IsolatedStorage> sınıfı üç salt okunurdur özellikler sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>ve <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="036a5-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="036a5-108">Bu özellikleri, mağazaya yazmanın izin verilen en fazla depolama boyutunun aşılmasına neden olup olmayacağını anlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="036a5-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="036a5-109">Yalıtılmış depolamaya aynı anda erişildiğini aklınızda bulundurun; Bu nedenle, kalan depolama miktarını hesaplarken, depolama alanı mağazaya yazmayı denediğinizde tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="036a5-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="036a5-110">Ancak, kullanılabilir depolama alanının üst sınırına ulaşılmaya ulaşılmadığını belirlemenize yardımcı olması için deponun en büyük boyutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="036a5-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="036a5-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> özelliği, derlemenin düzgün şekilde çalışması için olan kanıta bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="036a5-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="036a5-112">Bu nedenle, bu özelliği yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi kullanılarak oluşturulan <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesneler üzerinde almalısınız.</span><span class="sxs-lookup"><span data-stu-id="036a5-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="036a5-113">başka herhangi bir şekilde oluşturulmuş nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile> (örneğin, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yönteminden döndürülen nesneler), doğru en büyük boyutu döndürmez.</span><span class="sxs-lookup"><span data-stu-id="036a5-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="036a5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="036a5-114">Example</span></span>

<span data-ttu-id="036a5-115">Aşağıdaki kod örneği yalıtılmış bir depo edinir, birkaç dosya oluşturur ve <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> özelliğini alır.</span><span class="sxs-lookup"><span data-stu-id="036a5-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="036a5-116">Kalan alan bayt cinsinden raporlanır.</span><span class="sxs-lookup"><span data-stu-id="036a5-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="036a5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="036a5-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="036a5-118">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="036a5-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="036a5-119">Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma</span><span class="sxs-lookup"><span data-stu-id="036a5-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
