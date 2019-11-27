---
title: 'Nasıl Yapılır: Dizin Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348806"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dizin Oluşturma

Dizinler oluşturmak için `My.Computer.FileSystem` nesnesinin `CreateDirectory` yöntemini kullanın.  
  
 Dizin zaten varsa, hiçbir özel durum oluşturulmaz.  
  
### <a name="to-create-a-directory"></a>Bir dizin oluşturmak için  
  
- Dizinin oluşturulması gereken konumun tam yolunu belirterek `CreateDirectory` yöntemini kullanın. Bu örnek, Dizin `NewDirectory` `C:\Documents and Settings\All Users\Documents`oluşturur.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dizin adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).  
  
- Oluşturulacak dizinin üst dizini salt okunurdur (<xref:System.IO.IOException>).  
  
- Dizin adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Dizin adı iki nokta üst üste ":" (<xref:System.NotSupportedException>).  
  
- Kullanıcının dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).  
  
- Kullanıcının kısmi güven durumunda izinleri eksik (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
