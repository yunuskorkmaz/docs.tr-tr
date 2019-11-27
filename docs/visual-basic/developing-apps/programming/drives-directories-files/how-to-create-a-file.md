---
title: 'Nasıl Yapılır: Dosya Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348792"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Oluşturma

Bu örnek, <xref:System.IO.File> sınıfındaki <xref:System.IO.File.Create%2A> yöntemi kullanılarak belirtilen yolda boş bir metin dosyası oluşturur.  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  

 Dosyaya yazmak için `file` değişkenini kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Dosya zaten varsa, değiştirilmiştir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).  
  
- Yol salt okunurdur (<xref:System.IO.IOException>).  
  
- Yol adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Yol adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).  
  
- Yol yalnızca bir iki nokta üst üste ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Kısmi güven ortamlarında bir <xref:System.Security.SecurityException> oluşturulabilir.  
  
 <xref:System.IO.File.Create%2A> metoduna yapılan çağrı <xref:System.Security.Permissions.FileIOPermission>gerektirir.  
  
 Kullanıcının dosyayı oluşturma izni yoksa bir <xref:System.UnauthorizedAccessException> oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Kısmen güvenilen koddan kitaplıkları kullanma](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Kod erişim güvenliği temelleri](../../../../framework/misc/code-access-security-basics.md)
