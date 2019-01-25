---
title: "Nasıl yapılır: Visual Basic'te dosyayı yeniden adlandırma"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3b1e85cc9e0b0768f7065ff690f6dc969ee040b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676373"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosyayı yeniden adlandırma
Kullanım `RenameFile` yöntemi `My.Computer.FileSystem` geçerli konumu, dosya adı ve yeni dosya adı sağlayarak bir dosyayı yeniden adlandırmak için nesne. Bu yöntem, bir dosyayı taşımak için kullanılamaz; kullanma `MoveFile` yöntemi taşımak ve dosyayı yeniden adlandırın.  
  
### <a name="to-rename-a-file"></a>Bir dosyayı yeniden adlandırmak için  
  
-   Kullanım `My.Computer.FileSystem.RenameFile` bir dosyayı yeniden adlandırmak için yöntemi. Bu örnek adlı dosyayı yeniden adlandırır `Test.txt` için `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de, kod parçacığında bulunan **dosya sistemi - işleme sürücüler, klasörler ve dosyaları**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   `newName` yol bilgisi içerir (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `newName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).  
  
-   Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Varolan bir dosya veya dizin belirtilen ada sahip olduğundan `newName` (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Nasıl yapılır: Dosya taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Nasıl yapılır: Aynı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl yapılır: Farklı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
