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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348816"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma

Dosyaları kopyalamak için `My.Computer.FileSystem.CopyFile` yöntemini kullanın. Parametreler var olan dosyaların üzerine yazılmasına, dosyayı yeniden adlandırmanıza, işlemin ilerlemesini göstermeye ve kullanıcının işlemi iptal edebilmesini sağlar.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aynı klasörde bir dosyanın kopyasını oluşturmak için  
  
- Hedef dosyayı ve konumu sağlayarak `CopyFile` yöntemini kullanın. Aşağıdaki örnek, `test2.txt`adlı `test.txt` bir kopyasını oluşturur.  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Varolan dosyaların üzerine yazarak aynı klasörde bir dosyanın kopyasını oluşturmak için  
  
- Hedef dosyayı ve konumu sağlayarak `CopyFile` yöntemini kullanın ve `overwrite` `True`olarak ayarlama. Aşağıdaki örnek, `test2.txt` adlı bir `test.txt` kopyası oluşturur ve var olan tüm dosyaları bu adla geçersiz kılar.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.  
  
- Sistem mutlak yolu alamadı (<xref:System.ArgumentException>).  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.  
  
- Kaynak dosya geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
- Birleşik yol, var olan bir dizine işaret eder (<xref:System.IO.IOException>).  
  
- Hedef dosya vardır ve `overwrite` `False` (<xref:System.IO.IOException>) olarak ayarlanır.  
  
- Kullanıcı, dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.IO.IOException>).  
  
- Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- `ShowUI` `True`olarak ayarlanır `onUserCancel` `ThrowException`olarak ayarlanır ve Kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).  
  
- `ShowUI` `True`olarak ayarlanır `onUserCancel` `ThrowException`olarak ayarlanır ve belirtilmemiş g/ç hatası oluşur (<xref:System.OperationCanceledException>).  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
- Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl Yapılır: Bir Dizini Diğerine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
