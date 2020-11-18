---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 47421b4ab223a0c68a7449ba58fd010ef6f7ccab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830785"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="440bd-102">Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme</span><span class="sxs-lookup"><span data-stu-id="440bd-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="440bd-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>Sınıfı yalıtılmış depolama dosyalarını silmek için iki yöntem sunar:</span><span class="sxs-lookup"><span data-stu-id="440bd-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="440bd-104">Örnek yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve bunu çağıran depoyu siler.</span><span class="sxs-lookup"><span data-stu-id="440bd-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="440bd-105">Bu işlem için izin gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="440bd-105">No permissions are required for this operation.</span></span> <span data-ttu-id="440bd-106">Mağazaya erişebilen tüm kodlar, içindeki verilerin herhangi birini veya tümünü silebilir.</span><span class="sxs-lookup"><span data-stu-id="440bd-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="440bd-107">Statik yöntem, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değerini alır ve kodu çalıştıran kullanıcının tüm depolarını siler.</span><span class="sxs-lookup"><span data-stu-id="440bd-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="440bd-108">Bu işlem <xref:System.Security.Permissions.IsolatedStorageFilePermission> değer için izin gerektiriyor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .</span><span class="sxs-lookup"><span data-stu-id="440bd-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="440bd-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="440bd-109">Example</span></span>  
 <span data-ttu-id="440bd-110">Aşağıdaki kod örneği, statik ve örnek yöntemlerinin kullanımını gösterir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> .</span><span class="sxs-lookup"><span data-stu-id="440bd-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="440bd-111">Sınıfı iki depo edinir; biri Kullanıcı ve derleme için yalıtılmıştır ve diğeri Kullanıcı, etki alanı ve derleme için yalıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="440bd-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="440bd-112">Kullanıcı, etki alanı ve derleme deposu daha sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama dosyasının yöntemi çağırarak silinir  `isoStore1` .</span><span class="sxs-lookup"><span data-stu-id="440bd-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="440bd-113">Ardından, kullanıcının tüm geri kalan depoları statik yöntem çağırarak silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> .</span><span class="sxs-lookup"><span data-stu-id="440bd-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="440bd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="440bd-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="440bd-115">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="440bd-115">Isolated Storage</span></span>](isolated-storage.md)
