---
description: ': Nasıl yapılır: Visual Basic dosya yollarını ayrıştırma hakkında daha fazla bilgi edinin'
title: 'Nasıl yapılır: Dosya Yollarını Ayrıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: dff423679324974d64c613a292c253d99d668c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797503"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma

<xref:Microsoft.VisualBasic.FileIO.FileSystem>Nesnesi, dosya yollarını ayrıştırırken bazı yararlı yöntemler sunar.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>Yöntemi iki yol alır ve düzgün şekilde biçimlendirilen Birleşik yolu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A>Yöntemi, belirtilen yolun üst öğesinin mutlak yolunu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>Yöntemi, <xref:System.IO.FileInfo> dosyanın adı ve yolu gibi özelliklerinin belirlenmesi için sorgulanabilen bir nesne döndürür.  
  
 Dosya adı uzantısına bağlı olarak dosyanın içeriğiyle ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
### <a name="to-determine-a-files-name-and-path"></a>Bir dosyanın adını ve yolunu belirleme  
  
- <xref:System.IO.FileInfo.DirectoryName%2A> <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> Bir dosyanın adını ve yolunu öğrenmek için nesnesinin ve özelliklerini kullanın. Bu örnek, adı ve yolu belirler ve görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Tam yolu oluşturmak üzere bir dosyanın adını ve dizinini birleştirmek için  
  
- `CombinePath`Dizinini, dizin ve adı sağlayarak kullanın. Bu örnek, dizeleri alır `folderPath` ve `fileName` Önceki örnekte oluşturulur, bunları birleştirir ve sonucu görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma](how-to-get-the-collection-of-files-in-a-directory.md)
