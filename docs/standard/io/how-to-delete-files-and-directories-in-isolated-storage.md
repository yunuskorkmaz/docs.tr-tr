---
title: "Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme"
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cd17b85dbdc9315654d042e18d28fbfd0e2dcc52
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="3ad33-102">Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme</span><span class="sxs-lookup"><span data-stu-id="3ad33-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="3ad33-103">Dizinleri ve dosyaları bir yalıtılmış depolama dosyasında silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ad33-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="3ad33-104">Bir depo içindeki dosya ve dizin adları işletim sistemi bağımlıdır ve kök sanal dosya sistemi gibi göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3ad33-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="3ad33-105">Bunlar Windows işletim sistemlerinde büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="3ad33-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="3ad33-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Sınıf, dizinleri ve dosyaları silmek için iki yöntem sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ad33-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="3ad33-107">Bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> bir dosya veya dizin yok silmeye çalışırsanız özel durum.</span><span class="sxs-lookup"><span data-stu-id="3ad33-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="3ad33-108">Adında bir joker karakter içeriyorsa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> oluşturur bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> oluşturur bir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="3ad33-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="3ad33-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Dizin herhangi bir dosya veya alt dizinler içeriyorsa yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3ad33-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="3ad33-110">Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> var olan dosyaları ve dizinleri almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3ad33-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="3ad33-111">Sanal dosya sisteminde bir deposu arama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bul var olan dosyaları ve dizinleri yalıtılmış depolamadaki](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="3ad33-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ad33-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ad33-112">Example</span></span>  
 <span data-ttu-id="3ad33-113">Aşağıdaki kod örneği oluşturur ve birkaç dizinleri ve dosyaları siler.</span><span class="sxs-lookup"><span data-stu-id="3ad33-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3ad33-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ad33-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="3ad33-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="3ad33-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
