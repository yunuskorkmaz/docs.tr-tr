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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707534"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="5559f-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="5559f-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="5559f-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static metodunu kullanarak geçerli kullanıcı için tüm yalıtılmış depoları numaralandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5559f-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="5559f-104">Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değeri alır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile> bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5559f-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="5559f-105">Depoları listelemek için, <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değerini belirten <xref:System.Security.Permissions.IsolatedStorageFilePermission> izninizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5559f-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="5559f-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemini <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değeriyle çağırırsanız, geçerli kullanıcı için tanımlanan <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnelerinin bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5559f-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5559f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5559f-107">Example</span></span>  
 <span data-ttu-id="5559f-108">Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir mağaza edinir, birkaç dosya oluşturur ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi kullanılarak bu dosyaları alır.</span><span class="sxs-lookup"><span data-stu-id="5559f-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5559f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5559f-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="5559f-110">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="5559f-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
