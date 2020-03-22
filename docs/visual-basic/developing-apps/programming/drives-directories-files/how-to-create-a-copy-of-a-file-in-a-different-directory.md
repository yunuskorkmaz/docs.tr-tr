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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348838"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma

Yöntem, `My.Computer.FileSystem.CopyFile` dosyaları kopyalamanızı sağlar. Parametreleri, varolan dosyaların üzerine yazma, dosyayı yeniden adlandırma, işlemin ilerlemesini gösterme ve kullanıcının işlemi iptal etmesine izin verme olanağı sağlar.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Metin dosyasını başka bir klasöre kopyalamak için  
  
- Kaynak `CopyFile` dosya ve hedef dizini belirterek bir dosyayı kopyalamak için yöntemi kullanın. Parametre, `overwrite` varolan dosyaların üzerine yazıp yazılmayacağınızı belirtmenize olanak tanır. Aşağıdaki kod örnekleri nasıl `CopyFile`kullanılacağını gösterir.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
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
- [Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl Yapılır: Bir Dizini Diğerine Kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
