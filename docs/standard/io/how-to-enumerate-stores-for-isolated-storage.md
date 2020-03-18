---
title: 'Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707534"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="e0e37-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="e0e37-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="e0e37-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> Statik yöntemi kullanarak geçerli kullanıcı için tüm yalıtılmış depoları sayısalatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e37-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="e0e37-104">Bu yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageScope> bir değer <xref:System.IO.IsolatedStorage.IsolatedStorageFile> alır ve bir sayısallaştırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0e37-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="e0e37-105">Depoları sayısallandırmak için, <xref:System.Security.Permissions.IsolatedStorageFilePermission> <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri belirten izne sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e0e37-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="e0e37-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> Yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değeri olan bir yöntem olarak çağırırsanız, geçerli kullanıcı için tanımlanan bir dizi <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0e37-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e37-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0e37-107">Example</span></span>  
 <span data-ttu-id="e0e37-108">Aşağıdaki kod örneği, kullanıcı ve derleme tarafından yalıtılmış bir depo alır, birkaç dosya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> oluşturur ve yöntemi kullanarak bu dosyaları alır.</span><span class="sxs-lookup"><span data-stu-id="e0e37-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e0e37-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0e37-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="e0e37-110">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="e0e37-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
