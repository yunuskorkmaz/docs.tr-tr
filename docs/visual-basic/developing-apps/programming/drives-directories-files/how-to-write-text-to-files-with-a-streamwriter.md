---
title: 'Nasıl yapılır: StreamWriter ile Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 373f3bd07ea61263ddd81037d8cbbb06f789e599
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411583"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te StreamWriter ile Dosyalara Metin Yazma

Bu örnek <xref:System.IO.StreamWriter> , yöntemi ile bir nesnesi açar `My.Computer.FileSystem.OpenTextFileWriter` ve onu sınıfının yöntemiyle bir metin dosyasına bir dize yazmak için kullanır <xref:System.IO.TextWriter.WriteLine%2A> <xref:System.IO.StreamWriter> .  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya var ve salt okunurdur ( <xref:System.IO.IOException> ).  
  
- Disk dolu ( <xref:System.IO.IOException> ).  
  
- Yol adı çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasöre erişmesi gerekir. Dosya zaten mevcutsa, uygulamanın yalnızca daha `Write` az bir ayrıcalığa erişmesi gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve `Read` `Create` bir klasör için erişim yerine yalnızca tek bir dosyaya erişim izni verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Nasıl yapılır: metin dosyalarından okuma](how-to-read-from-text-files.md)
- [Dosyalara Yazma](writing-to-files.md)
