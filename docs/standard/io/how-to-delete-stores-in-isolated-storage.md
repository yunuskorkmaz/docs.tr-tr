---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme'
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
ms.openlocfilehash: 6b1e8e651fd8e18c79dd629c154fb6c4d74243e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707833"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="6971b-102">Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme</span><span class="sxs-lookup"><span data-stu-id="6971b-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="6971b-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı yalıtılmış depolama dosyalarını silmek için iki yöntem sunar:</span><span class="sxs-lookup"><span data-stu-id="6971b-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="6971b-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> örnek yöntemi herhangi bir bağımsız değişken almaz ve bunu çağıran mağazayı siler.</span><span class="sxs-lookup"><span data-stu-id="6971b-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="6971b-105">Bu işlem için izin gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6971b-105">No permissions are required for this operation.</span></span> <span data-ttu-id="6971b-106">Mağazaya erişebilen tüm kodlar, içindeki verilerin herhangi birini veya tümünü silebilir.</span><span class="sxs-lookup"><span data-stu-id="6971b-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="6971b-107">Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değerini alır ve kodu çalıştıran kullanıcının tüm depolarını siler.</span><span class="sxs-lookup"><span data-stu-id="6971b-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="6971b-108">Bu işlem, <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri için <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6971b-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6971b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6971b-109">Example</span></span>  
 <span data-ttu-id="6971b-110">Aşağıdaki kod örneği, statik ve örnek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6971b-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="6971b-111">Sınıfı iki depo edinir; biri Kullanıcı ve derleme için yalıtılmıştır ve diğeri Kullanıcı, etki alanı ve derleme için yalıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6971b-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="6971b-112">Kullanıcı, etki alanı ve derleme deposu daha sonra yalıtılmış depolama dosyasının <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yöntemi çağırarak silinir `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="6971b-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="6971b-113">Sonra, Kullanıcı için kalan tüm depolar <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>statik yöntem çağırarak silinir.</span><span class="sxs-lookup"><span data-stu-id="6971b-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6971b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6971b-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="6971b-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="6971b-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
