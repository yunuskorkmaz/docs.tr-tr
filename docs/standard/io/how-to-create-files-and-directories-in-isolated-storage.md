---
title: 'Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: 83e8c800dc74d9689f1bfdb506a6b454e87b36ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707876"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="6307c-102">Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6307c-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="6307c-103">Yalıtılmış bir depo elde ettikten sonra, veri depolamak için dizinler ve dosyalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6307c-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="6307c-104">Bir mağaza içinde, dosya ve dizin adları sanal dosya sisteminin köküne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6307c-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="6307c-105">Dizin oluşturmak için örnek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6307c-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="6307c-106">Var olmayan bir dizinin alt dizinini belirtirseniz, her iki dizin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6307c-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="6307c-107">Zaten var olan bir dizini belirtirseniz, yöntem dizin oluşturmadan döndürür ve özel durum atılmaz.</span><span class="sxs-lookup"><span data-stu-id="6307c-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="6307c-108">Ancak, geçersiz karakterler içeren bir dizin adı belirtirseniz, bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="6307c-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="6307c-109">Dosya oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6307c-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6307c-110">Windows işletim sisteminde, yalıtılmış depolama dosyası ve dizin adları büyük/küçük harf duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="6307c-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="6307c-111">Diğer bir tanesi, adlı `ThisFile.txt`bir dosya oluşturur ve `THISFILE.TXT`ardından başka bir dosya oluşturursanız, yalnızca bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6307c-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="6307c-112">Dosya adı, orijinal kasasını görüntü amacıyla tutar.</span><span class="sxs-lookup"><span data-stu-id="6307c-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6307c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6307c-113">Example</span></span>  
 <span data-ttu-id="6307c-114">Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulup oluşturulabildiğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6307c-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6307c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6307c-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="6307c-116">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="6307c-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
