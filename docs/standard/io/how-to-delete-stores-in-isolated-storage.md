---
title: "Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme"
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
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ae04deeb8d23b496a9111b0d4b5b68e12ac1439
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="60493-102">Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme</span><span class="sxs-lookup"><span data-stu-id="60493-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="60493-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı yalıtılmış depolama dosyaları silmek için iki yöntem sunar:</span><span class="sxs-lookup"><span data-stu-id="60493-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="60493-104">Örnek yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve çağırır deposu siler.</span><span class="sxs-lookup"><span data-stu-id="60493-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="60493-105">Bu işlem için yok izinleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60493-105">No permissions are required for this operation.</span></span> <span data-ttu-id="60493-106">Deposuna erişebilecek herhangi bir kod tüm veriler içindeki silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60493-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="60493-107">Statik yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> geçen <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değeri ve silme kod kullanan kullanıcı için tüm depolar.</span><span class="sxs-lookup"><span data-stu-id="60493-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="60493-108">Bu işlem gerektirir <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri.</span><span class="sxs-lookup"><span data-stu-id="60493-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60493-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="60493-109">Example</span></span>  
 <span data-ttu-id="60493-110">Aşağıdaki kod örneğinde statik kullanımını ve örneği gösterilmektedir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="60493-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="60493-111">Sınıfın iki depoları alır; Kullanıcı ve derleme için yalıtılmış biridir ve diğer kullanıcı, etki alanı ve derleme için ayrı tutulur.</span><span class="sxs-lookup"><span data-stu-id="60493-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="60493-112">Kullanıcı, etki alanı ve derleme deposu çağırarak ardından silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama dosyasının yöntemini `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="60493-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="60493-113">Ardından, kullanıcı için tüm kalan depolarını statik yöntemini çağırarak silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="60493-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="60493-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60493-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="60493-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="60493-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
