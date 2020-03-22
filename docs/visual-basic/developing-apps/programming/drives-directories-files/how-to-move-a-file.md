---
title: 'Nasıl Yapılır: Dosya Taşıma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335367"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Taşıma

Yöntem, `My.Computer.FileSystem.MoveFile` bir dosyayı başka bir klasöre taşımak için kullanılabilir. Hedef yapı yoksa, oluşturulur.  
  
### <a name="to-move-a-file"></a>Dosyayı taşımak için  
  
- Hem `MoveFile` kaynak dosya hem de hedef dosya için dosya adını ve konumunu belirterek dosyayı taşımak için yöntemi kullanın. Bu örnek, adlı `test.txt` `TestDir1` dosyayı `TestDir2`. Kaynak dosya adı ile aynı olmasına rağmen hedef dosya adının belirtildiğini unutmayın.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Bir dosyayı taşımak ve yeniden adlandırmak için  
  
- Dosyayı `MoveFile` taşımak için, kaynak dosya adını ve konumunu, hedef konumu ve hedef konumdaki yeni adı belirterek yöntemi kullanın. Bu örnek, adlı `test.txt` `TestDir1` dosyayı taşır `TestDir2` `nexttest.txt`ve yeniden adlandırır.  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- `destinationFileName`veya `Nothing` boş bir<xref:System.ArgumentNullException>dize ( ).  
  
- Kaynak dosya geçerli değil veya yok<xref:System.IO.FileNotFoundException>( ).  
  
- Birleştirilmiş yol varolan bir dizine işaret `overwrite` eder, `False`hedef dosya vardır ve hedef dizinde aynı ada sahip bir dosya kullanılıyor veya kullanıcının<xref:System.IO.IOException>dosyaya erişmek için yeterli izine sahip olmadığı ( ) ayarlanır.  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- `showUI`ayarlanır `True`, `onUserCancel` olarak ayarlanır `ThrowException`ve ya kullanıcı işlemi iptal etti ya da belirtilmeyen bir<xref:System.OperationCanceledException>G/Ç hatası oluşur ( ).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
- Kullanıcının gerekli izni yoktur<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
