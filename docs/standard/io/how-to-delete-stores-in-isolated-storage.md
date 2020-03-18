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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707833"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="616d4-102">Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme</span><span class="sxs-lookup"><span data-stu-id="616d4-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="616d4-103">Sınıf, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> yalıtılmış depolama dosyalarını siler için iki yöntem sağlar:</span><span class="sxs-lookup"><span data-stu-id="616d4-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="616d4-104">Örnek yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve onu çağıran mağazayı siler.</span><span class="sxs-lookup"><span data-stu-id="616d4-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="616d4-105">Bu işlem için izin gerekmez.</span><span class="sxs-lookup"><span data-stu-id="616d4-105">No permissions are required for this operation.</span></span> <span data-ttu-id="616d4-106">Depoya erişebilen herhangi bir kod içindeki verileri veya tümünü silebilir.</span><span class="sxs-lookup"><span data-stu-id="616d4-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="616d4-107">Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> numaralandırma değerini alır <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> ve kodu çalıştıran kullanıcı için tüm depoları siler.</span><span class="sxs-lookup"><span data-stu-id="616d4-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="616d4-108">Bu <xref:System.Security.Permissions.IsolatedStorageFilePermission> <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> işlem, değer için izin gerektirir.</span><span class="sxs-lookup"><span data-stu-id="616d4-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="616d4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="616d4-109">Example</span></span>  
 <span data-ttu-id="616d4-110">Aşağıdaki kod örneği statik ve örnek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="616d4-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="616d4-111">Sınıf iki mağaza alır; biri kullanıcı ve derleme için yalıtılmış, diğeri kullanıcı, etki alanı ve derleme için yalıtılmış.</span><span class="sxs-lookup"><span data-stu-id="616d4-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="616d4-112">Kullanıcı, etki alanı ve montaj deposu sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama `isoStore1`dosyasının yöntemini arayarak silinir.</span><span class="sxs-lookup"><span data-stu-id="616d4-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="616d4-113">Daha sonra, kullanıcı için kalan tüm mağazalar <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>statik yöntem çağırılarak silinir.</span><span class="sxs-lookup"><span data-stu-id="616d4-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="616d4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="616d4-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="616d4-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="616d4-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
