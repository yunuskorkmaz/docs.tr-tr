---
title: 'Nasıl Yapılır: StreamWriter ile Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334493"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te StreamWriter ile Dosyalara Metin Yazma

Bu <xref:System.IO.StreamWriter> örnek, `My.Computer.FileSystem.OpenTextFileWriter` yöntemi ile bir nesnesi açar ve onu <xref:System.IO.TextWriter.WriteLine%2A> <xref:System.IO.StreamWriter> sınıfının yöntemiyle bir metin dosyasına bir dize yazmak için kullanır.  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya var ve salt okunurdur (<xref:System.IO.IOException>).  
  
- Disk dolu (<xref:System.IO.IOException>).  
  
- Yol adı çok uzun (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasöre erişmesi gerekir `Create` . Dosya zaten mevcutsa, uygulamanın yalnızca `Write` daha az bir ayrıcalığa erişmesi gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve bir klasör için `Read` `Create` erişim yerine yalnızca tek bir dosyaya erişim izni verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Nasıl yapılır: metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
