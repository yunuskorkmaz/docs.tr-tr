---
title: "Nasıl Yapılır: Visual Basic'te Dosya Oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 6167ea0850308eec4b558a47dd881476325a8ea1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584852"
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
 [Kod erişim güvenliği temelleri](../../../../framework/misc/code-access-security-basics.md)
