---
title: 'Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348816"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma

Dosyaları `My.Computer.FileSystem.CopyFile` kopyalamak için yöntemi kullanın. Parametreler, varolan dosyaların üzerine yazmanızı, dosyayı yeniden adlandırmanızı, işlemin ilerlemesini göstermenizi ve kullanıcının işlemi iptal etmesine izin verir.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aynı klasördeki bir dosyanın kopyasını oluşturmak için  
  
- Hedef `CopyFile` dosyayı ve konumu sağlayarak yöntemi kullanın. Aşağıdaki `test.txt` örnek, .. `test2.txt`  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Aynı klasördeki bir dosyanın kopyasını oluşturmak için varolan dosyaların üzerine yazma  
  
- Yöntemi kullanarak, hedef dosyayı ve konumu sağlama `True`ve '' a ayarlama `overwrite` `CopyFile` Aşağıdaki örnek, `test.txt` çağrılan `test2.txt` bir kopyasını oluşturur ve bu ada göre varolan dosyaların üzerine yazar.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durum atılmasına neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Sistem mutlak yolu alamadım<xref:System.ArgumentException>( ).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Kaynak dosya geçerli değil veya yok<xref:System.IO.FileNotFoundException>( ).  
  
- Birleştirilmiş yol varolan bir<xref:System.IO.IOException>dizine işaret eder ( ).  
  
- Hedef dosya var `overwrite` ve `False` ayarlanır<xref:System.IO.IOException>( ).  
  
- Kullanıcının dosyaya erişmek için yeterli izinleri yoktur (<xref:System.IO.IOException>).  
  
- Hedef klasörde aynı ada sahip bir<xref:System.IO.IOException>dosya kullanılıyor ( ).  
  
- Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- `ShowUI`ayarlanır `True` `onUserCancel` , olarak ayarlanır `ThrowException`ve kullanıcı işlemi iptal etti<xref:System.OperationCanceledException>( ).  
  
- `ShowUI`ayarlanır `True` `onUserCancel` ve belirtilmemiş bir G/Ç hatası oluşur (<xref:System.OperationCanceledException>). `ThrowException`  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Kullanıcının gerekli izni yoktur<xref:System.UnauthorizedAccessException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl Yapılır: Bir Dizini Diğerine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
