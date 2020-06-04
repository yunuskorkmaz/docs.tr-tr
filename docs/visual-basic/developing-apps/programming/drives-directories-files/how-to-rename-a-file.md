---
title: 'Nasıl yapılır: Dosyayı Yeniden Adlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3de41ee6627315f0e26964b75f564ff98fe472ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411596"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosyayı Yeniden Adlandırma

`RenameFile` `My.Computer.FileSystem` Geçerli konumu, dosya adını ve yeni dosya adını sağlayarak bir dosyayı yeniden adlandırmak için nesnesinin yöntemini kullanın. Bu yöntem bir dosyayı taşımak için kullanılamaz; `MoveFile`dosyayı taşımak ve yeniden adlandırmak için yöntemini kullanın.  
  
### <a name="to-rename-a-file"></a>Bir dosyayı yeniden adlandırmak için  
  
- `My.Computer.FileSystem.RenameFile`Bir dosyayı yeniden adlandırmak için yöntemini kullanın. Bu örnek, olarak adlandırılan dosyayı yeniden adlandırır `Test.txt` `SecondTest.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide kod parçacığı, **dosya sistemi Işleme sürücülerinde, klasörlerinde ve dosyalarında**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- `newName`yol bilgilerini ( <xref:System.ArgumentException> ) içerir.  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- `newName``Nothing`ya da boş bir dizedir ( <xref:System.ArgumentNullException> ).  
  
- Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).  
  
- () İçinde belirtilen ada sahip bir dosya veya dizin var `newName` <xref:System.IO.IOException> .  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
- Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Nasıl yapılır: Dosya Taşıma](how-to-move-a-file.md)
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](creating-deleting-and-moving-files-and-directories.md)
- [Nasıl yapılır: Aynı Dizinde Dosya Kopyası Oluşturma](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
