---
title: 'Nasıl yapılır: dizinleri kopyalama'
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
ms.openlocfilehash: 5d40db7f902dac8bd6bbdc1510be8e56a321be30
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159461"
---
# <a name="how-to-copy-directories"></a>Nasıl yapılır: dizinleri kopyalama
Bu konu, bir dizinin içeriğini farklı bir konuma eşzamanlı olarak kopyalamak için g/ç sınıflarının nasıl kullanılacağını gösterir.

Zaman uyumsuz dosya kopyalama örneği için bkz. [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).

Bu örnekte, `DirectoryCopy` yönteminin `copySubDirs` `true`olarak ayarlanarak alt dizinler kopyalanır. `DirectoryCopy` yöntemi, kopyalamak daha fazla olana kadar alt dizinleri her alt dizine çağırarak özyinelemeli olarak kopyalar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
- [Ortak g/ç görevleri](../../../docs/standard/io/common-i-o-tasks.md)
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)
