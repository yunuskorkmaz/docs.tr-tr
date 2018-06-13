---
title: Dosya bir bayt dizisine okunamayacak kadar büyük
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 1b04d47cab77269a0ce84ef77c162a4401d99d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585931"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="6662c-102">Dosya bir bayt dizisine okunamayacak kadar büyük</span><span class="sxs-lookup"><span data-stu-id="6662c-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="6662c-103">Bir bayt dizisine okunamayacak kadar çalıştığınız dosya boyutu 4 GB aşıyor.</span><span class="sxs-lookup"><span data-stu-id="6662c-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="6662c-104">`My.Computer.FileSystem.ReadAllBytes` Yöntemi bu boyuttan daha büyük bir dosya okunamaz.</span><span class="sxs-lookup"><span data-stu-id="6662c-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6662c-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6662c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6662c-106">Kullanım bir <xref:System.IO.StreamReader> dosya okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="6662c-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="6662c-107">Daha fazla bilgi için bkz: [temelleri, .NET Framework dosyası g/ç ve dosya sistemi (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="6662c-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6662c-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6662c-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="6662c-109">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="6662c-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="6662c-110">Nasıl Yapılır: StreamReader Olan Dosyalardan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="6662c-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
