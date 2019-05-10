---
title: Dosya bir bayt dizisine okunamayacak kadar büyük
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: a842205e9184355e4ea750ea2eb32e4bcf05a14d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665112"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="5c277-102">Dosya bir bayt dizisine okunamayacak kadar büyük</span><span class="sxs-lookup"><span data-stu-id="5c277-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="5c277-103">4 GB bir bayt dizisine okunamayacak kadar çalıştığınız dosya boyutunu aşıyor.</span><span class="sxs-lookup"><span data-stu-id="5c277-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="5c277-104">`My.Computer.FileSystem.ReadAllBytes` Yöntemi, bu boyutu aşan bir dosya okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="5c277-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c277-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5c277-105">To correct this error</span></span>  
  
- <span data-ttu-id="5c277-106">Kullanım bir <xref:System.IO.StreamReader> dosyası okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="5c277-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="5c277-107">Daha fazla bilgi için [temelleri, .NET Framework dosyası g/ç ve dosya sistemi (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="5c277-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c277-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c277-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="5c277-109">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="5c277-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="5c277-110">Nasıl yapılır: StreamReader olan dosyalardaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="5c277-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
