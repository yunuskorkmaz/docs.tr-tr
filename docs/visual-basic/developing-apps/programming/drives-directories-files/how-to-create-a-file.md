---
description: 'Hakkında daha fazla bilgi için: nasıl yapılır: Visual Basic dosya oluşturma'
title: 'Nasıl yapılır: Dosya Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: b46786035c14021ceb27cce5b34eff5c8397fc9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797594"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Oluşturma

Bu örnek, sınıfındaki yöntemini kullanarak belirtilen yolda boş bir metin dosyası oluşturur <xref:System.IO.File.Create%2A> <xref:System.IO.File> .  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 `file`Dosyaya yazmak için değişkenini kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Dosya zaten varsa, değiştirilmiştir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> ) içeriyor.  
  
- Yol salt okunurdur ( <xref:System.IO.IOException> ).  
  
- Yol adı `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Yol adı çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
- Yol geçersiz ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- Yol yalnızca bir iki nokta üst üste ":" ( <xref:System.NotSupportedException> ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 <xref:System.Security.SecurityException>Kısmi güven ortamlarında bir oluşturulur.  
  
 Yöntemine yapılan çağrı <xref:System.IO.File.Create%2A> gerekir <xref:System.Security.Permissions.FileIOPermission> .  
  
 <xref:System.UnauthorizedAccessException>Kullanıcının dosyayı oluşturma izni yoksa oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Kısmen Güvenilen Koddan Kitaplıkları Kullanma](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Kod Erişim Güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md)
