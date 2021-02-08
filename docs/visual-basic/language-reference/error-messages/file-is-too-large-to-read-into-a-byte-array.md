---
description: 'Hakkında daha fazla bilgi edinin: dosya bir bayt dizisine okunamayacak kadar büyük'
title: Dosya bir bayt dizisine okunamayacak kadar büyük
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 8b2eb7bcbbea42c56d607147e55d6c02695c5670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796294"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="89c44-103">Dosya bir bayt dizisine okunamayacak kadar büyük</span><span class="sxs-lookup"><span data-stu-id="89c44-103">File is too large to read into a byte array</span></span>

<span data-ttu-id="89c44-104">Bir bayt dizisine okumaya çalıştığınız dosyanın boyutu 4 GB 'ı aşıyor.</span><span class="sxs-lookup"><span data-stu-id="89c44-104">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="89c44-105">`My.Computer.FileSystem.ReadAllBytes`Yöntem bu boyutu aşan bir dosyayı okuyamıyor.</span><span class="sxs-lookup"><span data-stu-id="89c44-105">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89c44-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="89c44-106">To correct this error</span></span>  
  
- <span data-ttu-id="89c44-107"><xref:System.IO.StreamReader>Dosyayı okumak için bir kullanın.</span><span class="sxs-lookup"><span data-stu-id="89c44-107">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="89c44-108">Daha fazla bilgi için bkz. [.NET Framework dosya g/ç 'Nin temelleri ve dosya sistemi (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="89c44-108">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c44-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89c44-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="89c44-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="89c44-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="89c44-111">Nasıl yapılır: StreamReader Olan Dosyalardan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="89c44-111">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
