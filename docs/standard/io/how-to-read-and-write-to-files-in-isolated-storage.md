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
ms.openlocfilehash: 9aecf7aef9023439e145d408e40fb4adf5c0e986
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875427"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="6fd62-102">Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="6fd62-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="6fd62-103">Okuma veya yazma için bir yalıtılmış depodaki bir dosya kullanın bir <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> bir akış okuyucusunu nesnesiyle (<xref:System.IO.StreamReader> nesne) veya akış yazıcı (<xref:System.IO.StreamWriter> nesne).</span><span class="sxs-lookup"><span data-stu-id="6fd62-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd62-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6fd62-104">Example</span></span>  
 <span data-ttu-id="6fd62-105">Aşağıdaki kod örneği, bir yalıtılmış depolama alır ve TestStore.txt adlı bir dosya deposunda mevcut olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="6fd62-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="6fd62-106">Yoksa, dosyayı oluşturur ve "Merhaba yalıtılmış depolama" yazar.</span><span class="sxs-lookup"><span data-stu-id="6fd62-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="6fd62-107">TestStore.txt zaten varsa, örnek kod dosyasından okur.</span><span class="sxs-lookup"><span data-stu-id="6fd62-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6fd62-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fd62-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- <xref:System.IO.FileMode?displayProperty=nameWithType>  
- <xref:System.IO.FileAccess?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader?displayProperty=nameWithType>  
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
- [<span data-ttu-id="6fd62-109">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="6fd62-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="6fd62-110">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="6fd62-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
