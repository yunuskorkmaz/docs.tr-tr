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
ms.openlocfilehash: 732f121e6b1977a960cab207f8d56cd2a551383c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291870"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="169c5-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="169c5-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="169c5-103">Statik yöntemi kullanarak geçerli kullanıcı için yalıtılmış tüm depoları sıralayabilirsiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="169c5-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="169c5-104">Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değer alır ve bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="169c5-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="169c5-105">Depoları listelemek için, <xref:System.Security.Permissions.IsolatedStorageFilePermission> değeri belirten izninizin olması gerekir <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .</span><span class="sxs-lookup"><span data-stu-id="169c5-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="169c5-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>Yöntemini değeri ile çağırırsanız <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> , <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesne dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="169c5-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="169c5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="169c5-107">Example</span></span>  
 <span data-ttu-id="169c5-108">Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir mağaza edinir, birkaç dosya oluşturur ve yöntemini kullanarak bu dosyaları alır <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="169c5-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="169c5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="169c5-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="169c5-110">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="169c5-110">Isolated Storage</span></span>](isolated-storage.md)
