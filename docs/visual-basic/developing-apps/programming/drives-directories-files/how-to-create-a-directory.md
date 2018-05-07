---
title: "Nasıl Yapılır: Visual Basic'te Dizin Oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: ec9ee01e17f116e80708dbcb34e4d804bf3d7a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dizin Oluşturma
Kullanım `CreateDirectory` yöntemi `My.Computer.FileSystem` dizin oluşturmak için nesne.  
  
 Dizini zaten varsa, hiçbir özel durum oluşur.  
  
### <a name="to-create-a-directory"></a>Bir dizin oluşturmak için  
  
-   Kullanım `CreateDirectory` burada dizin oluşturulmalıdır konumunun tam yolunu belirterek yöntemi. Bu örnek dizinini oluşturur `NewDirectory` içinde `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dizin adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).  
  
-   Oluşturulacak dizininin üst dizini salt okunurdur (<xref:System.IO.IOException>).  
  
-   Dizin adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Dizin adı bir iki nokta üst üste olan ":" (<xref:System.NotSupportedException>).  
  
-   Kullanıcının, dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).  
  
-   Kullanıcı bir kısmi güven durumda izinlerine sahip değildir (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
