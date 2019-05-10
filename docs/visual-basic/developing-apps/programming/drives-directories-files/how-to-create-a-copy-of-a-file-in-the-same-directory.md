---
title: "Nasıl yapılır: Visual Basic'te aynı dizinde dosya kopyası oluşturma"
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 747d985cbd9e2f2cc7f9b07f5723455a63a87b8f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629090"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te aynı dizinde dosya kopyası oluşturma
Kullanım `My.Computer.FileSystem.CopyFile` dosyaları kopyalamak için yöntemi. Parametreleri, mevcut dosyaların üzerine yaz, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal olanak tanır.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aynı klasörde bir dosyanın bir kopyasını oluşturmak için  
  
- Kullanım `CopyFile` yöntemi, hedef dosya ve konumu belirtin. Aşağıdaki örnek, bir kopyasını oluşturur. `test.txt` adlı `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Varolan dosyaların üzerine aynı klasörde bir dosyanın bir kopyasını oluşturmak için  
  
- Kullanım `CopyFile` konumu ve hedef dosya sağlayan ve ayarı yöntemi `overwrite` için `True`. Aşağıdaki örnek, bir kopyasını oluşturur. `test.txt` adlı `test2.txt` ve var olan dosyalar bu adla üzerine yazar.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar, bir özel durum oluşturulmasına neden:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Sistem mutlak yolu alınamadı (<xref:System.ArgumentException>).  
  
- Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
- Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
- Birleşik yolun mevcut bir dizine işaret (<xref:System.IO.IOException>).  
  
- Hedef dosya var ve `overwrite` ayarlanır `False` (<xref:System.IO.IOException>).  
  
- Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.IO.IOException>).  
  
- Hedef klasörde aynı adda bir dosya kullanımda (<xref:System.IO.IOException>).  
  
- Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
- `ShowUI` ayarlanır `True`, `onUserCancel` ayarlanır `ThrowException`, ve kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).  
  
- `ShowUI` ayarlanır `True`, `onUserCancel` ayarlanır `ThrowException`, belirtilmeyen bir g/ç hatası oluşur (<xref:System.OperationCanceledException>).  
  
- Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
- Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Nasıl yapılır: Belirli bir düzendeki dosyaları dizine kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Nasıl yapılır: Farklı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl yapılır: Bir dizini diğerine kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl yapılır: Dosyayı yeniden adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
