---
title: 'Nasıl Yapılır: Dosya Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348792"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Oluşturma

Bu örnek, <xref:System.IO.File.Create%2A> <xref:System.IO.File> sınıftayöntemi kullanarak belirtilen yolda boş bir metin dosyası oluşturur.  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Dosyaya `file` yazmak için değişkeni kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Dosya zaten varsa, değiştirilir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol adı yanlış biçimlendirilmiş. Örneğin, yasadışı karakterler içerir veya sadece beyaz<xref:System.ArgumentException>boşluk ( ).  
  
- Yol salt okunur (<xref:System.IO.IOException>).  
  
- Yol adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Yol adı çok uzun<xref:System.IO.PathTooLongException>( ).  
  
- Yol geçersizdir (<xref:System.IO.DirectoryNotFoundException>).  
  
- Yol sadece bir kolon<xref:System.NotSupportedException>":" ( ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Kısmi <xref:System.Security.SecurityException> güven ortamlarında a atılabilir.  
  
 <xref:System.IO.File.Create%2A> Yönteme çağrı gerektirir. <xref:System.Security.Permissions.FileIOPermission>  
  
 Kullanıcının dosyayı oluşturma izni yoksa bir <xref:System.UnauthorizedAccessException> atma yapılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Kısmen Güvenilen Koddan Kitaplıkları Kullanma](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Kod Erişim Güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md)
