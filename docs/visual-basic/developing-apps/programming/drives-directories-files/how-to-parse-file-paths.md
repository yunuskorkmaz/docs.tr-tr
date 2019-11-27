---
title: 'Nasıl Yapılır: Dosya Yollarını Ayrıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335345"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma

<xref:Microsoft.VisualBasic.FileIO.FileSystem> nesnesi, dosya yollarını ayrıştırırken bazı yararlı yöntemler sunar.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> yöntemi iki yol alır ve düzgün şekilde biçimlendirilen Birleşik yolu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> yöntemi, belirtilen yolun üst öğesinin mutlak yolunu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> yöntemi, dosyanın adı ve yolu gibi özelliklerini belirleyebilmek için sorgulanabilen bir <xref:System.IO.FileInfo> nesnesi döndürür.  
  
 Dosya adı uzantısına bağlı olarak dosyanın içeriğiyle ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
### <a name="to-determine-a-files-name-and-path"></a>Bir dosyanın adını ve yolunu belirleme  
  
- Bir dosyanın adını ve yolunu öğrenmek için <xref:System.IO.FileInfo> nesnesinin <xref:System.IO.FileInfo.DirectoryName%2A> ve <xref:System.IO.FileInfo.Name%2A> özelliklerini kullanın. Bu örnek, adı ve yolu belirler ve görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Tam yolu oluşturmak üzere bir dosyanın adını ve dizinini birleştirmek için  
  
- Dizin ve adı sağlayarak `CombinePath` yöntemini kullanın. Bu örnek `folderPath` dizeleri alır ve önceki örnekte oluşturulan `fileName`, birleştirir ve sonucu görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
