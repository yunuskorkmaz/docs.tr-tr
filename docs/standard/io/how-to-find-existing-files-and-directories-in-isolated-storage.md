---
title: 'Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 866be7970c43051dd7e2bf8d45ae779aca130a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574884"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="0fd08-102">Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="0fd08-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="0fd08-103">Yalıtılmış Depolama dizinde aramak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fd08-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0fd08-104">Bu yöntem, bir arama deseniyle temsil eden bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="0fd08-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="0fd08-105">Tek karakter (?) ve çok karakter (\*) kullanabilirsiniz joker karakter arama deseni, ancak joker karakterler adının son bölümü görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fd08-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="0fd08-106">Örneğin, `directory1/*ect*` geçerli bir arama dizesi ancak `*ect*/directory2` değil.</span><span class="sxs-lookup"><span data-stu-id="0fd08-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="0fd08-107">Bir dosyayı aramak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fd08-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0fd08-108">Uygulandığı öğe arama dizelerini joker karakterleri için kısıtlama <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> için de geçerlidir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fd08-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="0fd08-109">Bu yöntemlerin hiçbiri yinelemeli; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, tüm dizinler veya deponuza dosyaları listeleme için herhangi bir yöntem sağlamanız değil.</span><span class="sxs-lookup"><span data-stu-id="0fd08-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="0fd08-110">Ancak, yinelemeli yöntemler aşağıdaki kod örneğinde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0fd08-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fd08-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fd08-111">Example</span></span>  
 <span data-ttu-id="0fd08-112">Aşağıdaki kod örneğinde dosyaları ve dizinleri yalıtılmış bir depolama alanına nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fd08-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="0fd08-113">İlk olarak, kullanıcı, etki alanı ve derleme için yalıtılmış bir deposu alınır ve bulundukları `isoStore` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0fd08-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="0fd08-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Yöntemi birkaç farklı dizinler, ayarlamak için kullanılır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Oluşturucusu bu dizinleri bazı dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0fd08-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="0fd08-115">Kod ardından sonuçları döngü `GetAllDirectories` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fd08-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="0fd08-116">Bu yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> geçerli dizindeki tüm dizin adlarını bulmak için.</span><span class="sxs-lookup"><span data-stu-id="0fd08-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="0fd08-117">Bu adları bir dizide depolanır ve ardından `GetAllDirectories` kendisini bulduğu her dizin için geçirme çağırır.</span><span class="sxs-lookup"><span data-stu-id="0fd08-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="0fd08-118">Sonuç olarak, tüm dizin adlarını dizi olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0fd08-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="0fd08-119">Ardından, kod çağırır `GetAllFiles` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fd08-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="0fd08-120">Bu yöntemi çağırır `GetAllDirectories` tüm adlarını bulmak için dizinleri ve ardından onu denetler dosyaları için her bir dizin kullanarak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fd08-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="0fd08-121">Görüntü için bir dizi sonuç döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0fd08-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0fd08-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0fd08-122">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="0fd08-123">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="0fd08-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
