---
title: 'Nasıl yapılır: Dosya ve dizinleri yalıtılmış depolamadaki Sil'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538030"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="f11b8-102">Nasıl yapılır: Dosya ve dizinleri yalıtılmış depolamadaki Sil</span><span class="sxs-lookup"><span data-stu-id="f11b8-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="f11b8-103">Dizinleri ve bir yalıtılmış depolama dosyasında dosyaları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f11b8-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="f11b8-104">Bir depo içindeki dosya ve dizin adları, işletim sistemi bağımlıdır ve köküne sanal dosya sistemi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f11b8-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="f11b8-105">Bunlar, Windows işletim sistemlerinde büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f11b8-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="f11b8-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Sınıf dizinleri ve dosyaları silmek için iki yöntem sunar: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="f11b8-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="f11b8-107">Bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu, bir dosya veya dizin yok silmeye çalışırsanız oluşur.</span><span class="sxs-lookup"><span data-stu-id="f11b8-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="f11b8-108">Adı, bir joker karakter içeriyorsa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> oluşturur bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> oluşturur bir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="f11b8-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="f11b8-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Dizin herhangi bir dosya veya alt dizinler içeriyorsa yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f11b8-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="f11b8-110">Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> mevcut dosya ve dizinleri almak için yöntemler.</span><span class="sxs-lookup"><span data-stu-id="f11b8-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="f11b8-111">Sanal dosya sisteminde bir deposunun arama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yalıtılmış depolamada mevcut dosya ve dizinleri bulma](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="f11b8-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f11b8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f11b8-112">Example</span></span>  
 <span data-ttu-id="f11b8-113">Aşağıdaki kod örneği oluşturur ve ardından çeşitli dizinleri ve dosyaları siler.</span><span class="sxs-lookup"><span data-stu-id="f11b8-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f11b8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f11b8-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="f11b8-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="f11b8-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
