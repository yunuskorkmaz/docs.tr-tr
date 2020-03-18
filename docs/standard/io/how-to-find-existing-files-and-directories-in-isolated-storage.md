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
ms.openlocfilehash: dfebcc9acf0b699f898c106921d15ce0294bc5d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707139"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="b19b7-102">Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="b19b7-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="b19b7-103">Yalıtılmış depolamada bir dizin <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> aramak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b19b7-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b19b7-104">Bu yöntem, bir arama deseni temsil eden bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="b19b7-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="b19b7-105">Arama deseninde hem tek karakterli (?) hem de çok karakterli (\*) joker karakter kullanabilirsiniz, ancak joker karakterin adın son bölümünde görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b19b7-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="b19b7-106">Örneğin, `directory1/*ect*` geçerli bir arama dizesi, ancak `*ect*/directory2` değildir.</span><span class="sxs-lookup"><span data-stu-id="b19b7-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="b19b7-107">Bir dosyayı aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b19b7-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b19b7-108">Arama dizeleri için geçerli olan joker karakter <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> kısıtlaması <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b19b7-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="b19b7-109">Bu yöntemlerin hiçbiri özyinelemeli değildir; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıf, mağazanızdaki tüm dizinleri veya dosyaları listelemek için herhangi bir yöntem sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b19b7-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="b19b7-110">Ancak, özyinelemeli yöntemler aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b19b7-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b19b7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b19b7-111">Example</span></span>  
 <span data-ttu-id="b19b7-112">Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulup oluşturulabildiğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b19b7-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="b19b7-113">İlk olarak, kullanıcı, etki alanı ve derleme için yalıtılmış `isoStore` bir mağaza alınır ve değişkene yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b19b7-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="b19b7-114">Yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> birkaç farklı dizinler ayarlamak için kullanılır <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> ve oluşturucu bu dizinlerde bazı dosyalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b19b7-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="b19b7-115">Kod daha sonra `GetAllDirectories` yöntemin sonuçları arasında döngüler.</span><span class="sxs-lookup"><span data-stu-id="b19b7-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="b19b7-116">Bu yöntem, geçerli dizindeki tüm dizin adlarını bulmak için kullanır. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A></span><span class="sxs-lookup"><span data-stu-id="b19b7-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="b19b7-117">Bu adlar bir dizide depolanır ve bulduğu `GetAllDirectories` her dizide geçerek kendisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b19b7-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="b19b7-118">Sonuç olarak, tüm dizin adları bir dizi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b19b7-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="b19b7-119">Sonra, kod `GetAllFiles` yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b19b7-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="b19b7-120">Bu yöntem, tüm dizinlerin adlarını bulmak için çağırır `GetAllDirectories` ve sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> yöntemi kullanarak dosyaları için her dizin denetler.</span><span class="sxs-lookup"><span data-stu-id="b19b7-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="b19b7-121">Sonuç görüntülenmek için bir dizi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b19b7-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b19b7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b19b7-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="b19b7-123">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="b19b7-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
