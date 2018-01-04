---
title: "Nasıl yapılır: Dizinleri Kopyalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 43e9027c1dbfc831f598991374c22434e01fe7ff
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-copy-directories"></a>Nasıl yapılır: Dizinleri Kopyalama
Bu örnekte, bir dizinin içeriklerini eşzamanlı olarak başka bir konuma kopyalamak için G/Ç sınıflarının nasıl kullanılacağı gösterilir. Bu örnekte, kullanıcı alt dizinlerin de kopyalanıp kopyalanmayacağını belirtebilir. Eğer alt dizinler kopyalanırsa bu örnekteki yöntem, başka bir kopyası kalmayana kadar sonraki her bir alt dizinde kendisini çağırarak yinelemeli olarak bu alt dizinleri kopyalar.  
  
 Dosyaları zaman uyumsuz olarak kopyalama ilişkin bir örnek için bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)  
 [Ortak G/Ç Görevleri](../../../docs/standard/io/common-i-o-tasks.md)  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)
