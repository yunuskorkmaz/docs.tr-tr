---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dizin oluşturma'
title: 'Nasıl yapılır: Dizin Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 39a0f1b2f482b27b6f207f0ca8a498db198e9d59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797607"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dizin Oluşturma

`CreateDirectory` `My.Computer.FileSystem` Dizin oluşturmak için nesnesinin yöntemini kullanın.  
  
 Dizin zaten varsa, hiçbir özel durum oluşturulmaz.  
  
### <a name="to-create-a-directory"></a>Bir dizin oluşturmak için  
  
- `CreateDirectory`Dizinin oluşturulması gereken konumun tam yolunu belirterek yöntemi kullanın. Bu örnek, dizininde dizinini `NewDirectory` oluşturur `C:\Documents and Settings\All Users\Documents` .  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dizin adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> ) içeriyor.  
  
- Oluşturulacak dizinin üst dizini salt okunurdur ( <xref:System.IO.IOException> ).  
  
- Dizin adı `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Dizin adı çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
- Dizin adı iki nokta üst üste ":" ( <xref:System.NotSupportedException> ).  
  
- Kullanıcının dizin oluşturma izni yok ( <xref:System.UnauthorizedAccessException> ).  
  
- Kullanıcının kısmi güven durumunda () izinleri yoktur <xref:System.Security.SecurityException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Dosya ve Dizin Oluşturma, Silme ve Taşıma](creating-deleting-and-moving-files-and-directories.md)
