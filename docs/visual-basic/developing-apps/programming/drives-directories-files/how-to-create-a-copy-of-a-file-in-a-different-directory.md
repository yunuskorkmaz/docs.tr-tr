---
title: 'Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348838"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma

`My.Computer.FileSystem.CopyFile` yöntemi, dosyaları kopyalamanızı sağlar. Parametreleri var olan dosyaların üzerine yazma, dosyayı yeniden adlandırma, işlemin ilerlemesini gösterme ve kullanıcının işlemi iptal edebilmesini sağlar.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Bir metin dosyasını başka bir klasöre kopyalamak için  
  
- Bir kaynak dosya ve hedef dizin belirterek bir dosyayı kopyalamak için `CopyFile` yöntemini kullanın. `overwrite` parametresi, var olan dosyaların üzerine yazılıp yazılmayacağını belirtmenize olanak tanır. Aşağıdaki kod örnekleri `CopyFile`nasıl kullanacağınızı göstermektedir.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
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
- [Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl Yapılır: Bir Dizini Diğerine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
