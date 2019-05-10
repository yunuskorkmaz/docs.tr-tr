---
title: "Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 3b4f74836b32fea0e5c24fd4500581f17e39cd4c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623140"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma
Bu örnek açılır bir <xref:System.IO.StreamWriter> nesnesi ile `My.Computer.FileSystem.OpenTextFileWriter` yöntemi ve bir dize içeren bir metin dosyası yazmak için kullandığı <xref:System.IO.TextWriter.WriteLine%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya var ve salt okunur (<xref:System.IO.IOException>).  
  
- Disk dolu (<xref:System.IO.IOException>).  
  
- Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulamayı gerekli `Create` klasörü için erişim. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişim, daha az ayrıcalıkla. Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` tek bir dosyaya erişimi yerine `Create` erişim için bir klasör.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Nasıl yapılır: Metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
