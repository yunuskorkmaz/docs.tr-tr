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

Dizinoluşturmak için `My.Computer.FileSystem` nesnenin `CreateDirectory` yöntemini kullanın.  
  
 Dizin zaten varsa, özel durum atılmaz.  
  
### <a name="to-create-a-directory"></a>Dizin oluşturmak için  
  
- Dizinin `CreateDirectory` oluşturulması gereken konumun tam yolunu belirterek yöntemi kullanın. Bu örnek, `NewDirectory` ''de `C:\Documents and Settings\All Users\Documents`dizin oluşturur.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dizin adı yanlış biçimlendirilmiş. Örneğin, yasadışı karakterler içerir veya sadece beyaz<xref:System.ArgumentException>boşluk ( ).  
  
- Oluşturulacak dizinin üst dizini salt okunur (<xref:System.IO.IOException>).  
  
- Dizin adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Dizin adı çok uzun<xref:System.IO.PathTooLongException>( ).  
  
- Dizin adı bir kolon<xref:System.NotSupportedException>":" ( ).  
  
- Kullanıcının dizini oluşturma izni yoktur<xref:System.UnauthorizedAccessException>( ).  
  
- Kullanıcı kısmi güven durumunda izinlerden yoksundur<xref:System.Security.SecurityException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
