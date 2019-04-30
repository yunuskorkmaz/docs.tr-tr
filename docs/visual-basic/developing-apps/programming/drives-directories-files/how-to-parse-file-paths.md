---
title: "Nasıl yapılır: Visual Basic'te dosya yollarını ayrıştırma"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: c089910e3fd5d02b674cfed3062fb15275d91486
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672516"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosya yollarını ayrıştırma
<xref:Microsoft.VisualBasic.FileIO.FileSystem> Nesnesi, dosya yolları ayrıştırılırken çeşitli kullanışlı yöntemler sunar.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Yöntemi iki yolu alır ve düzgün şekilde biçimlendirilmiş bir birleşik yolunu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Yöntemi üst öğesinin sağlanan yol mutlak yolu döndürür.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Yöntemi döndürür bir <xref:System.IO.FileInfo> adı ve yolu gibi dosya özelliklerini belirlemek için sorgulanabilir bir nesne.  
  
 Dosya adı uzantısına göre dosyasının içeriği hakkında kararlar yapmayın. Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
### <a name="to-determine-a-files-name-and-path"></a>Bir dosyanın adı ve yolu belirlemek için  
  
- Kullanım <xref:System.IO.FileInfo.DirectoryName%2A> ve <xref:System.IO.FileInfo.Name%2A> özelliklerini <xref:System.IO.FileInfo> bir dosyanın adı ve yolu belirlemek için nesne. Bu örnek adını ve yolunu belirler ve bunları görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Bir dosyanın adı ve tam yolunu oluşturulacağı dizin birleştirmek için  
  
- Kullanım `CombinePath` yöntemi, dizin ve ad sağlama. Bu örnek, dizeleri alan `folderPath` ve `fileName` önceki örnekte oluşturulan, bunları bir araya getirir ve sonucu görüntüler.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
