---
title: "Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma"
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
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="af418-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="af418-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="af418-103">Geçerli kullanıcı için tüm yalıtılmış depoları kullanarak numaralandırabilir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> statik yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af418-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="af418-104">Bu yöntem alır bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değeri ve döndürür bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="af418-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="af418-105">Depoları numaralandırma için bilmeniz gereken <xref:System.Security.Permissions.IsolatedStorageFilePermission> belirtir izni <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri.</span><span class="sxs-lookup"><span data-stu-id="af418-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="af418-106">Çağırırsanız <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemiyle <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değer, bir dizi döndürür <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="af418-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af418-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="af418-107">Example</span></span>  
 <span data-ttu-id="af418-108">Aşağıdaki kod örneğinde, kullanıcı ve derlemeye göre yalıtılmış, birkaç dosyaları oluşturur ve bu dosyaları kullanarak alır bir mağaza edinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af418-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="af418-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af418-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="af418-110">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="af418-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
