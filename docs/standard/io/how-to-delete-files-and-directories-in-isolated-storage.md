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
ms.openlocfilehash: ec4de3e3a139cfcf66f1f6252c03c467f4ccfbc5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707863"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="db72e-102">Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme</span><span class="sxs-lookup"><span data-stu-id="db72e-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="db72e-103">Yalıtılmış bir depolama dosyası içindeki dizinleri ve dosyaları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db72e-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="db72e-104">Bir mağaza içinde, dosya ve Dizin adları işletim sistemine bağımlıdır ve sanal dosya sisteminin köküne göreli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="db72e-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="db72e-105">Windows işletim sistemlerinde büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="db72e-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="db72e-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> sınıfı dizinleri ve dosyaları silmek için iki yöntem sunar: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="db72e-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="db72e-107">Varolmayan bir dosyayı veya dizini silmeye çalıştığınızda bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="db72e-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="db72e-108">Ada bir joker karakter eklerseniz, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu atar ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> bir <xref:System.ArgumentException> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db72e-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="db72e-109">Dizin herhangi bir dosya veya alt dizin içeriyorsa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="db72e-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="db72e-110">Mevcut dosya ve dizinleri almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db72e-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="db72e-111">Bir deponun sanal dosya sistemini arama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yalıtılmış depolamada mevcut dosya ve dizinleri bulma](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="db72e-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db72e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="db72e-112">Example</span></span>  
 <span data-ttu-id="db72e-113">Aşağıdaki kod örneği, birkaç dizin ve dosyayı oluşturur ve siler.</span><span class="sxs-lookup"><span data-stu-id="db72e-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="db72e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db72e-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="db72e-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="db72e-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
