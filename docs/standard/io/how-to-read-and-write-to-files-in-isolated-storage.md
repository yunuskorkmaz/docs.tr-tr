---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90195e4e1a368f8b8b0fcf04fd8d86afce3ea7c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573782"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="ce80b-102">Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="ce80b-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="ce80b-103">Okuma veya, bir yalıtılmış depolama dosyasında yazmak için kullanın bir <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> bir akış okuyucusunu nesnesiyle (<xref:System.IO.StreamReader> nesnesi) veya akış yazıcı (<xref:System.IO.StreamWriter> nesnesi).</span><span class="sxs-lookup"><span data-stu-id="ce80b-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce80b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce80b-104">Example</span></span>  
 <span data-ttu-id="ce80b-105">Aşağıdaki kod örneğinde bir yalıtılmış depolamada alır ve TestStore.txt adlı bir dosya deposunda mevcut olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="ce80b-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="ce80b-106">Yoksa, bir dosya oluşturur ve "Merhaba yalıtılmış depolama" dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="ce80b-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="ce80b-107">TestStore.txt zaten varsa, örnek kod dosyasından okur.</span><span class="sxs-lookup"><span data-stu-id="ce80b-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ce80b-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce80b-108">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 <xref:System.IO.FileMode?displayProperty=nameWithType>  
 <xref:System.IO.FileAccess?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader?displayProperty=nameWithType>  
 <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
 [<span data-ttu-id="ce80b-109">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="ce80b-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="ce80b-110">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="ce80b-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
