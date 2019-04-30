---
title: 'Nasıl yapılır: Dizinleri kopyalama'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57e2b61fb8fef37234dc10885752f92e5f9b1330
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751936"
---
# <a name="how-to-copy-directories"></a>Nasıl yapılır: Dizinleri kopyalama
Bu konu, bir dizinin içeriklerini eşzamanlı olarak başka bir konuma kopyalanacak g/ç sınıflarını kullanmayı gösterir. 

Zaman uyumsuz dosya kopyalama örneği için bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md). 

Bu örnekte ayarlayarak alt dizinleri kopyalar `copySubDirs` , `DirectoryCopy` yönteme `true`. `DirectoryCopy` Kalmayana kadar fazla kopyalamak için kendisini her bir alt dizinde çağırarak yöntemi yinelemeli olarak alt dizinleri kopyalar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
- [Ortak g/ç görevleri](../../../docs/standard/io/common-i-o-tasks.md)
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)