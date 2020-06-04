---
title: 'Nasıl yapılır: Dosya Taşıma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 2dafeb3b5f8b8c3a8976b25c1a57f405aebb32b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401608"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Taşıma

`My.Computer.FileSystem.MoveFile`Yöntemi, bir dosyayı başka bir klasöre taşımak için kullanılabilir. Hedef yapı yoksa, oluşturulur.  
  
### <a name="to-move-a-file"></a>Bir dosyayı taşımak için  
  
- `MoveFile`Kaynak dosya ve hedef dosya için dosya adını ve konumunu belirterek dosyayı taşımak için yöntemini kullanın. Bu örnek, adlı dosyayı `test.txt` öğesine taşır `TestDir1` `TestDir2` . Hedef dosya adının, kaynak dosya adıyla aynı olmasına rağmen belirtildiğine unutmayın.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Bir dosyayı taşımak ve yeniden adlandırmak için  
  
- `MoveFile`Kaynak dosya adını ve konumunu, hedef konumu ve hedef konumdaki yeni adı belirterek dosyayı taşımak için yöntemini kullanın. Bu örnek, adlı dosyayı `test.txt` konumundan `TestDir1` öğesine taşır `TestDir2` ve yeniden adlandırır `nexttest.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- `destinationFileName``Nothing`ya da boş bir dizedir ( <xref:System.ArgumentNullException> ).  
  
- Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).  
  
- Birleşik yol, var olan bir dizine işaret eder, hedef dosya vardır ve `overwrite` olarak ayarlanır `False` , hedef dizinde aynı ada sahip bir dosya kullanımda olur veya kullanıcının dosyaya () erişmek için yeterli izni yoktur <xref:System.IO.IOException> .  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- `showUI`, olarak ayarlanır, olarak `True` `onUserCancel` ayarlanır `ThrowException` ve Kullanıcı işlemi iptal etti ya da belirtilmeyen g/ç hatası oluşur ( <xref:System.OperationCanceledException> ).  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
- Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Nasıl yapılır: Dosyayı Yeniden Adlandırma](how-to-rename-a-file.md)
- [Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl yapılır: Dosya Yollarını Ayrıştırma](how-to-parse-file-paths.md)
