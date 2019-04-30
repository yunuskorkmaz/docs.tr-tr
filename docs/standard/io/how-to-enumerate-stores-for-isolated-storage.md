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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f14259afe4ee296d930b042d9e9ef069a81e65f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751780"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="9a9eb-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="9a9eb-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="9a9eb-103">Geçerli kullanıcı için tüm yalıtılmış depoları kullanarak numaralandırabilirsiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> statik yöntem.</span><span class="sxs-lookup"><span data-stu-id="9a9eb-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="9a9eb-104">Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> döndürür ve değeri bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="9a9eb-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="9a9eb-105">Depoları numaralandırma için olmalıdır <xref:System.Security.Permissions.IsolatedStorageFilePermission> belirten izni <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri.</span><span class="sxs-lookup"><span data-stu-id="9a9eb-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="9a9eb-106">Eğer <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemiyle <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değer dizisi döndürür <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9a9eb-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a9eb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a9eb-107">Example</span></span>  
 <span data-ttu-id="9a9eb-108">Aşağıdaki kod örneği, kullanıcı ve derlemeye göre yalıtılır, birkaç dosya oluşturur ve bu dosyaları kullanarak alır bir depo alır <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a9eb-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9a9eb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a9eb-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="9a9eb-110">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="9a9eb-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
