---
title: 'Nasıl yapılır: dizinleri kopyalama'
description: Bir dizinin içeriğini eşzamanlı olarak başka bir konuma kopyalamak için g/ç sınıfları kullanarak dizinleri kopyalama konusuna bakın.
ms.date: 12/27/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: b81723b9ed7067826692e8383bf64058d4295f0c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830837"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="86d10-103">Nasıl yapılır: dizinleri kopyalama</span><span class="sxs-lookup"><span data-stu-id="86d10-103">How to: Copy directories</span></span>

<span data-ttu-id="86d10-104">Bu makalede, bir dizinin içeriğini farklı bir konuma eşzamanlı olarak kopyalamak için g/ç sınıflarının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86d10-104">This article demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="86d10-105">Zaman uyumsuz dosya kopyalama örneği için bkz. [zaman uyumsuz dosya g/ç](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="86d10-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="86d10-106">Bu örnekte, yönteminin öğesini olarak ayarlayarak alt dizinler kopyalanır `copySubDirs` `DirectoryCopy` `true` .</span><span class="sxs-lookup"><span data-stu-id="86d10-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="86d10-107">Bu `DirectoryCopy` Yöntem, kopyalamak daha fazla olana kadar alt dizinleri her alt dizine çağırarak özyinelemeli olarak kopyalar.</span><span class="sxs-lookup"><span data-stu-id="86d10-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d10-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="86d10-108">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="86d10-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86d10-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="86d10-110">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="86d10-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="86d10-111">Ortak G/Ç görevleri</span><span class="sxs-lookup"><span data-stu-id="86d10-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="86d10-112">Zaman uyumsuz dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="86d10-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
