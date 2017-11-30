---
title: "Nasıl Yapılır: Visual Basic'te Dosya Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Oluşturma
Bu örnek, belirtilen yolu kullanarak boş bir metin dosyası oluşturur <xref:System.IO.File.Create%2A> yönteminde <xref:System.IO.File> sınıfı.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kullanım `file` veya dosyaya yazmak için değişken.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dosya zaten mevcutsa değiştirilir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).  
  
-   Yolun salt okunurdur (<xref:System.IO.IOException>).  
  
-   Yol adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Yol adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 A <xref:System.Security.SecurityException> kısmi güven ortamlarında oluşturulur.  
  
 Çağrı <xref:System.IO.File.Create%2A> gerektirdiğine <xref:System.Security.Permissions.FileIOPermission>.  
  
 Bir <xref:System.UnauthorizedAccessException> kullanıcının dosyayı oluşturma izni yoksa oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [Kısmen güvenilen koddan kitaplıkları kullanma](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [Kod erişim güvenliği temelleri](https://msdn.microsoft.com/library/33tceax8)
