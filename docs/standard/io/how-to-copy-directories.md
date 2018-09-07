---
title: 'Nasıl yapılır: Dizinleri Kopyalama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 6f2c2fbd58b10af80a2a233cbd4211befe2dbd33
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075328"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="8e954-102">Nasıl yapılır: Dizinleri Kopyalama</span><span class="sxs-lookup"><span data-stu-id="8e954-102">How to: Copy Directories</span></span>
<span data-ttu-id="8e954-103">Bu örnekte, bir dizinin içeriklerini eşzamanlı olarak başka bir konuma kopyalamak için G/Ç sınıflarının nasıl kullanılacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8e954-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="8e954-104">Bu örnekte, kullanıcı alt dizinlerin de kopyalanıp kopyalanmayacağını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8e954-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="8e954-105">Eğer alt dizinler kopyalanırsa bu örnekteki yöntem, başka bir kopyası kalmayana kadar sonraki her bir alt dizinde kendisini çağırarak yinelemeli olarak bu alt dizinleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="8e954-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="8e954-106">Dosyaların eşzamansız kopyalanmasına bir örnek için bkz [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="8e954-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e954-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e954-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8e954-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e954-108">See also</span></span>

- <xref:System.IO.FileInfo>  
- <xref:System.IO.DirectoryInfo>  
- <xref:System.IO.FileStream>  
- [<span data-ttu-id="8e954-109">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="8e954-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="8e954-110">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="8e954-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
- [<span data-ttu-id="8e954-111">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="8e954-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
