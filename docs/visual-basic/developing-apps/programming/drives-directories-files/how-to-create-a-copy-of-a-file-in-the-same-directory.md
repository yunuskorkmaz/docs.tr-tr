---
title: "Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma"
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 1147e89292181060589b38be2972e2ff1a3e386c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588940"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma
Kullanım `My.Computer.FileSystem.CopyFile` dosyaları kopyalamak için yöntem. Parametreler, var olan dosyaların üzerine yazıp, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal izin ver olanak tanır.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aynı klasörde bir dosyanın bir kopyasını oluşturmak için  
  
-   Kullanım `CopyFile` yöntemi, hedef dosya ve konum belirtin. Aşağıdaki örnek, bir kopyasını oluşturur `test.txt` adlı `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Var olan dosyaların üzerine yazılması aynı klasörde bir dosyanın bir kopyasını oluşturmak için  
  
-   Kullanım `CopyFile` için bir hedef dosya ve konum sağlayarak ve ayarlama yöntemi `overwrite` için `True`. Aşağıdaki örnek, bir kopyasını oluşturur `test.txt` adlı `test2.txt` ve bu adı mevcut dosyaların üzerine yazar.  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar, bir özel durum oluşturulmasına neden olabilir:  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Sistem mutlak yolu alınamadı (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Birleşik yolu işaret ediyor. Varolan bir dizin (<xref:System.IO.IOException>).  
  
-   Hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False` (<xref:System.IO.IOException>).  
  
-   Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException>).  
  
-   Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).  
  
-   Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   `ShowUI` ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, ve kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).  
  
-   `ShowUI` ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, belirtilmeyen bir g/ç hatası nedeniyle oluşur (<xref:System.OperationCanceledException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Nasıl Yapılır: Bir Dizini Diğerine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
