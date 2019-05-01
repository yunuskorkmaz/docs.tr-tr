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
ms.openlocfilehash: 59a89aa354941b7ff22a125a980c2d9c75ac37ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947206"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma
Okuma veya yazma için bir yalıtılmış depodaki bir dosya kullanın bir <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> bir akış okuyucusunu nesnesiyle (<xref:System.IO.StreamReader> nesne) veya akış yazıcı (<xref:System.IO.StreamWriter> nesne).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir yalıtılmış depolama alır ve TestStore.txt adlı bir dosya deposunda mevcut olup olmadığını denetler. Yoksa, dosyayı oluşturur ve "Merhaba yalıtılmış depolama" yazar. TestStore.txt zaten varsa, örnek kod dosyasından okur.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
