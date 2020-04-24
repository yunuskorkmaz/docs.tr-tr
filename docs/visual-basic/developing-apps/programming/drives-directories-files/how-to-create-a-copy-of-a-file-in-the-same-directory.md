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

Dosyaları kopyalamak `My.Computer.FileSystem.CopyFile` için yöntemini kullanın. Parametreler var olan dosyaların üzerine yazılmasına, dosyayı yeniden adlandırmanıza, işlemin ilerlemesini göstermeye ve kullanıcının işlemi iptal edebilmesini sağlar.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aynı klasörde bir dosyanın kopyasını oluşturmak için  
  
- Hedef dosyayı `CopyFile` ve konumu sağlayarak yöntemini kullanın. Aşağıdaki örnek, `test.txt` çağrılan `test2.txt`bir kopyasını oluşturur.  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Varolan dosyaların üzerine yazarak aynı klasörde bir dosyanın kopyasını oluşturmak için  
  
- `CopyFile` Yöntemini kullanarak hedef dosya ve konumu ve olarak `overwrite` `True`ayarını yapın. Aşağıdaki örnek, `test.txt` adlı `test2.txt` bir kopyasını oluşturur ve bu ada göre var olan dosyaların üzerine yazar.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).  
  
- Sistem mutlak yolu (<xref:System.ArgumentException>) alamadı.  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.  
  
- Kaynak dosya geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
- Birleşik yol, var olan bir dizine (<xref:System.IO.IOException>) işaret eder.  
  
- Hedef dosya vardır ve `overwrite` ( `False` <xref:System.IO.IOException>) olarak ayarlanır.  
  
- Kullanıcı, dosyaya (<xref:System.IO.IOException>) erişmek için yeterli izinlere sahip değil.  
  
- Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- `ShowUI`olarak ayarlanır `True`, `onUserCancel` olarak ayarlanır `ThrowException`ve Kullanıcı işlemi (<xref:System.OperationCanceledException>) iptal etti.  
  
- `ShowUI``True`, `onUserCancel` olarak ayarlanır, olarak ayarlanır `ThrowException`ve belirtilmemiş g/ç hatası oluşur (<xref:System.OperationCanceledException>).  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Kullanıcı gerekli izne (<xref:System.UnauthorizedAccessException>) sahip değil.  
  
- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl Yapılır: Bir Dizini Diğerine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
