---
title: 'Nasıl Yapılır: Dizin Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348806"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dizin Oluşturma

Dizin oluşturmak `CreateDirectory` için `My.Computer.FileSystem` nesnesinin yöntemini kullanın.  
  
 Dizin zaten varsa, hiçbir özel durum oluşturulmaz.  
  
### <a name="to-create-a-directory"></a>Bir dizin oluşturmak için  
  
- Dizinin oluşturulması `CreateDirectory` gereken konumun tam yolunu belirterek yöntemi kullanın. Bu örnek, dizininde dizinini `NewDirectory` oluşturur `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dizin adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>) içeriyor.  
  
- Oluşturulacak dizinin üst dizini salt okunurdur (<xref:System.IO.IOException>).  
  
- Dizin adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Dizin adı iki nokta üst üste ":" (<xref:System.NotSupportedException>).  
  
- Kullanıcının dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).  
  
- Kullanıcının kısmi güven durumunda (<xref:System.Security.SecurityException>) izinleri yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
