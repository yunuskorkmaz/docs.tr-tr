---
title: 'Nasıl Yapılır: Dosya Yollarını Ayrıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335345"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma

Nesnesi <xref:Microsoft.VisualBasic.FileIO.FileSystem> , dosya yollarını ayrıştırırken bazı yararlı yöntemler sunar.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Yöntemi iki yol alır ve düzgün şekilde biçimlendirilen Birleşik yolu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Yöntemi, belirtilen yolun üst öğesinin mutlak yolunu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Yöntemi, dosyanın adı <xref:System.IO.FileInfo> ve yolu gibi özelliklerinin belirlenmesi için sorgulanabilen bir nesne döndürür.  
  
 Dosya adı uzantısına bağlı olarak dosyanın içeriğiyle ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
### <a name="to-determine-a-files-name-and-path"></a>Bir dosyanın adını ve yolunu belirleme  
  
- Bir dosyanın <xref:System.IO.FileInfo.DirectoryName%2A> adını <xref:System.IO.FileInfo.Name%2A> ve yolunu öğrenmek <xref:System.IO.FileInfo> için nesnesinin ve özelliklerini kullanın. Bu örnek, adı ve yolu belirler ve görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Tam yolu oluşturmak üzere bir dosyanın adını ve dizinini birleştirmek için  
  
- `CombinePath` Dizinini, dizin ve adı sağlayarak kullanın. Bu örnek, dizeleri `folderPath` alır ve `fileName` önceki örnekte oluşturulur, bunları birleştirir ve sonucu görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
