---
title: Dosya bir bayt dizisine okunamayacak kadar büyük
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 89459aaf766a70f69008f847dda7ac6e2a1e41d1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874193"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="6225a-102">Dosya bir bayt dizisine okunamayacak kadar büyük</span><span class="sxs-lookup"><span data-stu-id="6225a-102">File is too large to read into a byte array</span></span>

<span data-ttu-id="6225a-103">Bir bayt dizisine okumaya çalıştığınız dosyanın boyutu 4 GB 'ı aşıyor.</span><span class="sxs-lookup"><span data-stu-id="6225a-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="6225a-104">`My.Computer.FileSystem.ReadAllBytes`Yöntem bu boyutu aşan bir dosyayı okuyamıyor.</span><span class="sxs-lookup"><span data-stu-id="6225a-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6225a-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6225a-105">To correct this error</span></span>  
  
- <span data-ttu-id="6225a-106"><xref:System.IO.StreamReader>Dosyayı okumak için bir kullanın.</span><span class="sxs-lookup"><span data-stu-id="6225a-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="6225a-107">Daha fazla bilgi için bkz. [.NET Framework dosya g/ç 'Nin temelleri ve dosya sistemi (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="6225a-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6225a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6225a-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="6225a-109">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="6225a-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="6225a-110">Nasıl yapılır: StreamReader Olan Dosyalardan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="6225a-110">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
