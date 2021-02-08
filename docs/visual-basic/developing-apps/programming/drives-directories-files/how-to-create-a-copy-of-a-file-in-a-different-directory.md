---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic farklı bir dizinde dosya kopyası oluşturma'
title: 'Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 128a813ec3e5c759d5320d59a1e83f9d66af3bbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797646"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma

`My.Computer.FileSystem.CopyFile`Yöntemi, dosyaları kopyalamanızı sağlar. Parametreleri var olan dosyaların üzerine yazma, dosyayı yeniden adlandırma, işlemin ilerlemesini gösterme ve kullanıcının işlemi iptal edebilmesini sağlar.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Bir metin dosyasını başka bir klasöre kopyalamak için  
  
- `CopyFile`Kaynak dosya ve hedef dizin belirterek bir dosyayı kopyalamak için yöntemini kullanın. `overwrite`Parametresi, var olan dosyaların üzerine yazılıp yazılmayacağını belirtmenize izin verir. Aşağıdaki kod örnekleri, nasıl kullanılacağını göstermektedir `CopyFile` .  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Sistem mutlak yolu ( <xref:System.ArgumentException> ) alamadı.  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).  
  
- Birleşik yol, var olan bir dizine () işaret eder <xref:System.IO.IOException> .  
  
- Hedef dosya vardır ve `overwrite` () olarak ayarlanır `False` <xref:System.IO.IOException> .  
  
- Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.IO.IOException> .  
  
- Hedef klasörde aynı ada sahip bir dosya kullanımda ( <xref:System.IO.IOException> ).  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- `ShowUI` olarak ayarlanır `True` , olarak `onUserCancel` ayarlanır `ThrowException` ve Kullanıcı işlemi () iptal etti <xref:System.OperationCanceledException> .  
  
- `ShowUI` , olarak ayarlanır, olarak `True` `onUserCancel` ayarlanır `ThrowException` ve belirtilmemiş g/ç hatası oluşur ( <xref:System.OperationCanceledException> ).  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Nasıl yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Nasıl yapılır: Aynı Dizinde Dosya Kopyası Oluşturma](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Nasıl yapılır: Bir Dizini Diğerine Kopyalama](how-to-copy-a-directory-to-another-directory.md)
- [Nasıl yapılır: Dosyayı Yeniden Adlandırma](how-to-rename-a-file.md)
