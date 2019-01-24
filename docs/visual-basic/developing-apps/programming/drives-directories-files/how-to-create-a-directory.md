---
title: "Nasıl yapılır: Visual Basic'te bir dizin oluşturun"
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 878ba0b8f62c067101a73182a377f5cfcb84ebc2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527438"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te bir dizin oluşturun
Kullanım `CreateDirectory` yöntemi `My.Computer.FileSystem` dizinler oluşturmak için nesne.  
  
 Dizin zaten varsa, hiçbir özel durum oluşturulur.  
  
### <a name="to-create-a-directory"></a>Bir dizin oluşturmak için  
  
-   Kullanım `CreateDirectory` burada dizin oluşturulmalıdır konumun tam yolunu belirterek yöntemi. Bu örnek dizini `NewDirectory` içinde `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dizin adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).  
  
-   Oluşturulacak dizinin üst dizin salt okunur (<xref:System.IO.IOException>).  
  
-   Dizin adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Dizin adı iki nokta olan ":" (<xref:System.NotSupportedException>).  
  
-   Kullanıcının dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).  
  
-   Kullanıcı izinleri kısmi güven durumda eksik (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
