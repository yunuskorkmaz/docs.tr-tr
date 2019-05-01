---
title: "Nasıl yapılır: Visual Basic'te farklı dizinde dosya kopyası oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 25b9ff1e3a97acd69b6a885788dbc83ce19e71f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038330"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te farklı dizinde dosya kopyası oluşturma
`My.Computer.FileSystem.CopyFile` Yöntemi dosyaları kopyalamak sağlar. Parametrelerini varolan dosyaların üzerine yaz, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal etme olanağı sunar.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Bir metin dosyası başka bir klasöre kopyalamak için  
  
- Kullanım `CopyFile` yöntemi bir kaynak dosyası ve hedef dizini belirten bir dosyasını kopyalayın. `overwrite` Parametre, var olan dosyaların üzerine yazılıp yazılmayacağını belirtmenize olanak sağlar. Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
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
- [Nasıl yapılır: Aynı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl yapılır: Bir dizini diğerine kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Nasıl yapılır: Dosyayı yeniden adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
