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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707876"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="b5460-102">Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5460-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="b5460-103">Yalıtılmış bir mağaza elde ettikten sonra, verileri depolamak için dizin ve dosya oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5460-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="b5460-104">Bir mağaza içinde, dosya ve Dizin adları, sanal dosya sisteminin köküne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b5460-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="b5460-105">Bir dizin oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> örnek yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5460-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="b5460-106">Mevcut olmayan bir dizinin alt dizinini belirtirseniz, her iki dizin de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5460-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="b5460-107">Zaten var olan bir dizin belirtirseniz, yöntem bir dizin oluşturmadan geri döner ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="b5460-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="b5460-108">Ancak, geçersiz karakterler içeren bir dizin adı belirtirseniz bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5460-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="b5460-109">Bir dosya oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5460-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b5460-110">Windows işletim sisteminde, yalıtılmış depolama dosyası ve Dizin adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5460-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="b5460-111">Diğer bir deyişle, `ThisFile.txt`adlı bir dosya oluşturup `THISFILE.TXT`adlı başka bir dosya oluşturursanız, yalnızca bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5460-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="b5460-112">Dosya adı, görüntü amaçlarıyla orijinal büyük küçük harf durumunu korur.</span><span class="sxs-lookup"><span data-stu-id="b5460-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5460-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5460-113">Example</span></span>  
 <span data-ttu-id="b5460-114">Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b5460-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b5460-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5460-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="b5460-116">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="b5460-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
