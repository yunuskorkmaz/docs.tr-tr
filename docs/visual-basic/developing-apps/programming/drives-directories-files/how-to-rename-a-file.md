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

Geçerli konumu `RenameFile` , dosya adını `My.Computer.FileSystem` ve yeni dosya adını sağlayarak bir dosyayı yeniden adlandırmak için nesnesinin yöntemini kullanın. Bu yöntem bir dosyayı taşımak için kullanılamaz; dosyayı taşımak `MoveFile` ve yeniden adlandırmak için yöntemini kullanın.  
  
### <a name="to-rename-a-file"></a>Bir dosyayı yeniden adlandırmak için  
  
- Bir dosyayı `My.Computer.FileSystem.RenameFile` yeniden adlandırmak için yöntemini kullanın. Bu örnek, olarak `Test.txt` `SecondTest.txt`adlandırılan dosyayı yeniden adlandırır.  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide kod parçacığı, **dosya sistemi Işleme sürücülerinde, klasörlerinde ve dosyalarında**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).  
  
- `newName`yol bilgilerini (<xref:System.ArgumentException>) içerir.  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.  
  
- `newName``Nothing` ya da boş bir dizedir (<xref:System.ArgumentNullException>).  
  
- Kaynak dosya geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
- ( `newName` <xref:System.IO.IOException>) İçinde belirtilen ada sahip bir dosya veya dizin var.  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.  
  
- Kullanıcı gerekli izne (<xref:System.UnauthorizedAccessException>) sahip değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Nasıl Yapılır: Dosya Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
