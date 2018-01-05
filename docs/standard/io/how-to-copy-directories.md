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
# <a name="how-to-copy-directories"></a><span data-ttu-id="a2679-102">Nasıl yapılır: Dizinleri Kopyalama</span><span class="sxs-lookup"><span data-stu-id="a2679-102">How to: Copy Directories</span></span>
<span data-ttu-id="a2679-103">Bu örnekte, bir dizinin içeriklerini eşzamanlı olarak başka bir konuma kopyalamak için G/Ç sınıflarının nasıl kullanılacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a2679-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="a2679-104">Bu örnekte, kullanıcı alt dizinlerin de kopyalanıp kopyalanmayacağını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="a2679-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="a2679-105">Eğer alt dizinler kopyalanırsa bu örnekteki yöntem, başka bir kopyası kalmayana kadar sonraki her bir alt dizinde kendisini çağırarak yinelemeli olarak bu alt dizinleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a2679-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="a2679-106">Dosyaları zaman uyumsuz olarak kopyalama ilişkin bir örnek için bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="a2679-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2679-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2679-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a2679-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2679-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="a2679-109">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="a2679-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="a2679-110">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="a2679-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="a2679-111">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="a2679-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
