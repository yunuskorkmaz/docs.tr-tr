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
ms.openlocfilehash: f71f428037f33fdbc692ca2f02a4c767998d684e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288582"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="eba91-102">Nasıl yapılır: dizinleri kopyalama</span><span class="sxs-lookup"><span data-stu-id="eba91-102">How to: Copy directories</span></span>
<span data-ttu-id="eba91-103">Bu konu, bir dizinin içeriğini farklı bir konuma eşzamanlı olarak kopyalamak için g/ç sınıflarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eba91-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="eba91-104">Zaman uyumsuz dosya kopyalama örneği için bkz. [zaman uyumsuz dosya g/ç](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="eba91-104">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="eba91-105">Bu örnekte, yönteminin öğesini olarak ayarlayarak alt dizinler kopyalanır `copySubDirs` `DirectoryCopy` `true` .</span><span class="sxs-lookup"><span data-stu-id="eba91-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="eba91-106">Bu `DirectoryCopy` Yöntem, kopyalamak daha fazla olana kadar alt dizinleri her alt dizine çağırarak özyinelemeli olarak kopyalar.</span><span class="sxs-lookup"><span data-stu-id="eba91-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba91-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="eba91-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="eba91-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eba91-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="eba91-109">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="eba91-109">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="eba91-110">Ortak G/Ç görevleri</span><span class="sxs-lookup"><span data-stu-id="eba91-110">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="eba91-111">Zaman uyumsuz dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="eba91-111">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
