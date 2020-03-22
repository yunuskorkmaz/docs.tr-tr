---
title: 'Nasıl Yapılır: Dosyayı Yeniden Adlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334548"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosyayı Yeniden Adlandırma

Geçerli `RenameFile` konumu, `My.Computer.FileSystem` dosya adını ve yeni dosya adını sağlayarak dosyayı yeniden adlandırmak için nesnenin yöntemini kullanın. Bu yöntem bir dosyayı taşımak için kullanılamaz; dosyayı `MoveFile` taşımak ve yeniden adlandırmak için yöntemi kullanın.  
  
### <a name="to-rename-a-file"></a>Dosyayı yeniden adlandırmak için  
  
- Dosyayı `My.Computer.FileSystem.RenameFile` yeniden adlandırmak için yöntemi kullanın. Bu örnek, `Test.txt` `SecondTest.txt`'' adlı dosyayı yeniden adlandırır.  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet toplayıcı, snippet Dosya sisteminde yer alır **- İşleme Sürücüler, Klasörler ve Dosyalar**. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- `newName`yol bilgilerini<xref:System.ArgumentException>içerir ( ).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- `newName`veya `Nothing` boş bir<xref:System.ArgumentNullException>dize ( ).  
  
- Kaynak dosya geçerli değil veya yok<xref:System.IO.FileNotFoundException>( ).  
  
- () adlarında `newName` belirtilen varolan bir dosya<xref:System.IO.IOException>veya dizin vardır.  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
- Kullanıcı nın gerekli izni yoktur<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Nasıl Yapılır: Dosya Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
