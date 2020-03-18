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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707863"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="fe059-102">Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme</span><span class="sxs-lookup"><span data-stu-id="fe059-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="fe059-103">İznileri ve dosyaları yalıtılmış bir depolama dosyası içinde silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe059-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="fe059-104">Bir mağaza içinde, dosya ve dizin adları işletim sistemine bağlıdır ve sanal dosya sisteminin köküne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fe059-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="fe059-105">Windows işletim sistemlerinde büyük/küçük harf duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fe059-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="fe059-106">Sınıf, <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> dizinleri ve dosyaları silen <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>iki yöntem sağlar: ve.</span><span class="sxs-lookup"><span data-stu-id="fe059-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="fe059-107">Var <xref:System.IO.IsolatedStorage.IsolatedStorageException> olmayan bir dosyayı veya dizini silmeye çalışırsanız bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="fe059-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="fe059-108">Adına bir joker karakter eklerseniz, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> atar <xref:System.ArgumentException> ve bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="fe059-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="fe059-109">Dizin <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> herhangi bir dosya veya alt dizin içeriyorsa yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fe059-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="fe059-110">Varolan dosyaları <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> ve dizinleri almak için ve yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe059-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="fe059-111">Bir mağazanın sanal dosya sisteminde arama hakkında daha fazla bilgi için [bkz.](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)</span><span class="sxs-lookup"><span data-stu-id="fe059-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe059-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe059-112">Example</span></span>  
 <span data-ttu-id="fe059-113">Aşağıdaki kod örneği birkaç dizin ve dosya oluşturur ve sonra siler.</span><span class="sxs-lookup"><span data-stu-id="fe059-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fe059-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe059-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="fe059-115">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="fe059-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
