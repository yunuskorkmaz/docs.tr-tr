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

Bu örnek, <xref:System.IO.File.Create%2A> <xref:System.IO.File> sınıfındaki yöntemini kullanarak belirtilen yolda boş bir metin dosyası oluşturur.  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Dosyaya yazmak `file` için değişkenini kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Dosya zaten varsa, değiştirilmiştir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>) içeriyor.  
  
- Yol salt okunurdur (<xref:System.IO.IOException>).  
  
- Yol adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Yol adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).  
  
- Yol yalnızca bir iki nokta üst üste ":"<xref:System.NotSupportedException>().  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Kısmi <xref:System.Security.SecurityException> güven ortamlarında bir oluşturulur.  
  
 <xref:System.IO.File.Create%2A> Yöntemine yapılan çağrı gerekir <xref:System.Security.Permissions.FileIOPermission>.  
  
 <xref:System.UnauthorizedAccessException> Kullanıcının dosyayı oluşturma izni yoksa oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Kısmen Güvenilen Koddan Kitaplıkları Kullanma](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Kod Erişim Güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md)
