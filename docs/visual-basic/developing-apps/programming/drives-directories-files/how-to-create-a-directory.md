---
title: "Nasıl Yapılır: Visual Basic'te Dizin Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e4cd94113d77b2f4ff8127c80174107966ef360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Oluşturma, silme ve dosyaları ve dizinleri taşıma](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
