---
title: "Nasıl yapılır: Visual Basic'te dosya oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: e9eedb6dafdd181b254610331899b5df7ac0823f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661379"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosya oluşturma
Bu örnek, belirtilen yolu kullanarak boş bir metin dosyası oluşturur <xref:System.IO.File.Create%2A> yönteminde <xref:System.IO.File> sınıfı.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kullanım `file` dosyaya yazmak için değişken.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dosya zaten varsa, değiştirilir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).  
  
-   Salt okunur yoludur (<xref:System.IO.IOException>).  
  
-   Yol adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Yol adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 A <xref:System.Security.SecurityException> kısmi güven düzeyine sahip ortamlarda oluşturulabilir.  
  
 Çağrı <xref:System.IO.File.Create%2A> gerektirdiğine <xref:System.Security.Permissions.FileIOPermission>.  
  
 Bir <xref:System.UnauthorizedAccessException> kullanıcının dosyayı oluşturma izni yoksa oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Kısmen güvenilen koddan kitaplıkları kullanma](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Kod erişimi güvenliği temelleri](../../../../framework/misc/code-access-security-basics.md)
