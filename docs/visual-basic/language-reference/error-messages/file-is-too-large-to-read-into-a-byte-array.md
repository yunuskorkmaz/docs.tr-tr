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
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Dosya bir bayt dizisine okunamayacak kadar büyük

Bir bayt dizisine okumaya çalıştığınız dosyanın boyutu 4 GB 'ı aşıyor. `My.Computer.FileSystem.ReadAllBytes`Yöntem bu boyutu aşan bir dosyayı okuyamıyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- <xref:System.IO.StreamReader>Dosyayı okumak için bir kullanın. Daha fazla bilgi için bkz. [.NET Framework dosya g/ç 'Nin temelleri ve dosya sistemi (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Visual Basic ile Dosya Erişimi](../../developing-apps/programming/drives-directories-files/file-access.md)
- [Nasıl yapılır: StreamReader Olan Dosyalardan Metin Okuma](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
