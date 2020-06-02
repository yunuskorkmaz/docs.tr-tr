---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme'
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
ms.openlocfilehash: dc84fefbde1177993b17e9ec687a1ef759b74735
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291909"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="5d039-102">Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme</span><span class="sxs-lookup"><span data-stu-id="5d039-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="5d039-103">Yalıtılmış bir depolama dosyası içindeki dizinleri ve dosyaları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d039-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="5d039-104">Bir mağaza içinde, dosya ve Dizin adları işletim sistemine bağımlıdır ve sanal dosya sisteminin köküne göreli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5d039-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="5d039-105">Windows işletim sistemlerinde büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="5d039-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="5d039-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>Sınıfı dizinleri ve dosyaları silmek için iki yöntem sunar: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="5d039-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="5d039-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException>Mevcut olmayan bir dosyayı veya dizini silmeye çalışırsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d039-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="5d039-108">Adında bir joker karakter eklerseniz, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum oluşturur ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d039-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="5d039-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>Dizin herhangi bir dosya veya alt dizin içeriyorsa yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5d039-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="5d039-110"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> Mevcut dosya ve dizinleri almak için ve yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d039-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="5d039-111">Bir deponun sanal dosya sistemini arama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yalıtılmış depolamada mevcut dosya ve dizinleri bulma](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="5d039-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d039-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d039-112">Example</span></span>  
 <span data-ttu-id="5d039-113">Aşağıdaki kod örneği, birkaç dizin ve dosyayı oluşturur ve siler.</span><span class="sxs-lookup"><span data-stu-id="5d039-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5d039-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d039-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="5d039-115">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="5d039-115">Isolated Storage</span></span>](isolated-storage.md)
