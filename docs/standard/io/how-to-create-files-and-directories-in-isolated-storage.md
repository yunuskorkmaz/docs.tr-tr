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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08beb44fdb58ab1c1d53f70ac0653348b96fcb18
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886467"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="dfc8e-102">Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dfc8e-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="dfc8e-103">Bir yalıtılmış depolama aldıktan sonra dizin ve dosya verilerini depolamak için oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="dfc8e-104">Bir depo dosya ve dizin adları sanal dosya sisteminin kökünü göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="dfc8e-105">Bir dizin oluşturmak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> örnek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="dfc8e-106">Mevcut bir dizininin bir alt belirtirseniz, her iki dizini de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="dfc8e-107">Zaten bir dizin belirtirseniz, bir dizin oluşturmadan yöntemi döndürür ve hiçbir özel durum.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="dfc8e-108">Ancak, bir dizin adı belirtirseniz, geçersiz karakterler içeren bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="dfc8e-109">Bir dosya oluşturmak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dfc8e-110">Windows işletim sistemi, yalıtılmış depolama dosya ve dizin adlarını büyük küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="dfc8e-111">Diğer bir deyişle, adlı bir dosya oluşturursanız `ThisFile.txt`, ardından adlı başka bir dosya oluşturun `THISFILE.TXT`, tek bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="dfc8e-112">Dosya adı, kendi özgün büyük/küçük harfleri görüntüleme amacıyla tutar.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfc8e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfc8e-113">Example</span></span>  
 <span data-ttu-id="dfc8e-114">Aşağıdaki kod örneği bir yalıtılmış depoda dosyalar ve dizinler oluşturma işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dfc8e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc8e-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- [<span data-ttu-id="dfc8e-116">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="dfc8e-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
