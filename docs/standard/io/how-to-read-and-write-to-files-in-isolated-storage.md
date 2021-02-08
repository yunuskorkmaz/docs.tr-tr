---
description: 'Daha fazla bilgi edinin: nasıl yapılır: yalıtılmış depolamada dosyaları okuma ve yazma'
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 6e88cc4c590c44394768472ce8bd5fd89ac99d38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775545"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="14916-103">Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="14916-103">How to: Read and Write to Files in Isolated Storage</span></span>

<span data-ttu-id="14916-104">Yalıtılmış bir depodaki bir dosyayı okumak veya yazmak için, <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> Stream Reader ( <xref:System.IO.StreamReader> nesne) veya Stream Writer (nesne) ile bir nesne kullanın <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="14916-104">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14916-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="14916-105">Example</span></span>  

 <span data-ttu-id="14916-106">Aşağıdaki kod örneği yalıtılmış bir depo edinir ve TestStore.txt adlı bir dosyanın depoda mevcut olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="14916-106">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="14916-107">Yoksa, dosyayı oluşturur ve dosyaya "Hello yalıtılmış depolama" yazar.</span><span class="sxs-lookup"><span data-stu-id="14916-107">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="14916-108">TestStore.txt zaten varsa, örnek kod dosyadan okur.</span><span class="sxs-lookup"><span data-stu-id="14916-108">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="14916-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14916-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="14916-110">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="14916-110">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="14916-111">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="14916-111">Isolated Storage</span></span>](isolated-storage.md)
