---
title: 'Nasıl yapılsın: Dizinleri kopyalama'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159461"
---
# <a name="how-to-copy-directories"></a>Nasıl yapılsın: Dizinleri kopyalama
Bu konu, bir dizinin içeriğini başka bir konuma eşit olarak kopyalamak için G/Ç sınıflarının nasıl kullanılacağını gösterir.

Eşzamanlı dosya kopyalama örneği için Bkz. [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).

Bu örnek, `copySubDirs` `DirectoryCopy` yöntemin 'i ' ye `true`ayarlayarak alt dizinleri kopyalar. Yöntem, `DirectoryCopy` kopyalayane kadar her alt dizinde kendisini çağırarak alt dizinleri özyinelemeli olarak kopyalar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
- [Yaygın G/Ç görevleri](../../../docs/standard/io/common-i-o-tasks.md)
- [Asynchronous dosya I/O](../../../docs/standard/io/asynchronous-file-i-o.md)
