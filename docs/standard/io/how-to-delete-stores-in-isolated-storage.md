---
title: 'Nasıl yapılır: Yalıtılmış depolamadaki depoları silme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19a671cac609e79088956ecb4324ebb0a25fb941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547408"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="3c901-102">Nasıl yapılır: Yalıtılmış depolamadaki depoları silme</span><span class="sxs-lookup"><span data-stu-id="3c901-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="3c901-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı yalıtılmış depolama dosyalarının silinmesi için iki yöntem sunar:</span><span class="sxs-lookup"><span data-stu-id="3c901-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="3c901-104">Örnek yöntemini <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve çağrı yaptığı deposunu siler.</span><span class="sxs-lookup"><span data-stu-id="3c901-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="3c901-105">Bu işlem için gerekli izni yok.</span><span class="sxs-lookup"><span data-stu-id="3c901-105">No permissions are required for this operation.</span></span> <span data-ttu-id="3c901-106">Depoya erişebilir herhangi bir kod, tüm verileri içine silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c901-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="3c901-107">Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> alan <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değeri ve tüm depoları kodu çalıştıran kullanıcıyı siler.</span><span class="sxs-lookup"><span data-stu-id="3c901-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="3c901-108">Bu işlem gerektiriyor <xref:System.Security.Permissions.IsolatedStorageFilePermission> izinlerini <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri.</span><span class="sxs-lookup"><span data-stu-id="3c901-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c901-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c901-109">Example</span></span>  
 <span data-ttu-id="3c901-110">Aşağıdaki kod örneği statik kullanımını ve örnek gösterir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3c901-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="3c901-111">Sınıfı iki deposu alır; bir kullanıcı ve derlemeye için yalıtılmış ve diğer kullanıcı, etki alanı ve derleme için ayrı tutulur.</span><span class="sxs-lookup"><span data-stu-id="3c901-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="3c901-112">Kullanıcı, etki alanı ve derlemeye deponun çağırarak ardından silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama dosyasına yöntemi `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="3c901-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="3c901-113">Statik yöntemi çağırarak kullanıcı için tüm kalan depoları ardından silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="3c901-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3c901-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c901-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="3c901-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="3c901-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
