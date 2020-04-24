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

Yöntemi `My.Computer.FileSystem.MoveFile` , bir dosyayı başka bir klasöre taşımak için kullanılabilir. Hedef yapı yoksa, oluşturulur.  
  
### <a name="to-move-a-file"></a>Bir dosyayı taşımak için  
  
- Kaynak dosya `MoveFile` ve hedef dosya için dosya adını ve konumunu belirterek dosyayı taşımak için yöntemini kullanın. Bu örnek, adlı `test.txt` dosyayı `TestDir1` öğesine `TestDir2`taşır. Hedef dosya adının, kaynak dosya adıyla aynı olmasına rağmen belirtildiğine unutmayın.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Bir dosyayı taşımak ve yeniden adlandırmak için  
  
- Kaynak dosya `MoveFile` adını ve konumunu, hedef konumu ve hedef konumdaki yeni adı belirterek dosyayı taşımak için yöntemini kullanın. Bu örnek `test.txt` , adlı dosyayı konumundan `TestDir1` öğesine `TestDir2` taşır ve yeniden `nexttest.txt`adlandırır.  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.  
  
- `destinationFileName``Nothing` ya da boş bir dizedir (<xref:System.ArgumentNullException>).  
  
- Kaynak dosya geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
- Birleşik yol, var olan bir dizine işaret eder, hedef dosya vardır ve `overwrite` olarak `False`ayarlanır, hedef dizinde aynı ada sahip bir dosya kullanımda olur veya kullanıcının dosyaya (<xref:System.IO.IOException>) erişmek için yeterli izni yoktur.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- `showUI`, olarak ayarlanır, olarak ayarlanır `ThrowException`ve Kullanıcı işlemi iptal etti ya da belirtilmeyen g/ç hatası oluşur (<xref:System.OperationCanceledException>). `True` `onUserCancel`  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.  
  
- Kullanıcı gerekli izne (<xref:System.UnauthorizedAccessException>) sahip değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
