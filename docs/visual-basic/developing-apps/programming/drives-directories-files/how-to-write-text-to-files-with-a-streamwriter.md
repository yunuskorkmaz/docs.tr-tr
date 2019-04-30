---
title: "Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: ca792106bdd341fa4be8f3554ce70cd7d3f22522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772629"
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
