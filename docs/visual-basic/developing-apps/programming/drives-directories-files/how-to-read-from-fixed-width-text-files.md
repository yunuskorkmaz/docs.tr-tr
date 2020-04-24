---
title: 'Nasıl yapılır: sabit genişlikli metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334623"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic içindeki sabit genişlikli metin dosyalarından okuma

`TextFieldParser` Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.  
  
 `TextFieldType` Özelliği, ayrıştırılmış dosyanın ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları olduğunu tanımlar. Sabit genişlikli bir metin dosyasında, sonundaki alanın bir değişken genişliği olabilir. Uçtaki alanın bir değişken genişliğine sahip olduğunu belirtmek için, bu değeri sıfıra eşit veya daha küçük bir genişliğe sahip olacak şekilde tanımlayın.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Sabit genişlikli bir metin dosyasını ayrıştırmak için  
  
1. Yeni `TextFieldParser`bir oluştur. Aşağıdaki kod, `TextFieldParser` adlı adı `Reader` oluşturur ve dosyasını `test.log`açar.  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. `TextFieldType` Özelliği `FixedWidth`, genişliği ve biçimi tanımlayarak tanımlayın. Aşağıdaki kod, metnin sütunlarını tanımlar; Birincisi 5 karakter genişliğinde, ikinci 10, üçüncü 11 ve dördüncü değişken genişliktedir.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Dosyadaki alanlar arasında döngü gerçekleştirin. Herhangi bir satır bozuksa, bir hata bildirin ve ayrıştırmaya devam edin.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. `While` Ve `Using` bloklarıyla birlikte `End While` kapatın. `End Using`  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Örnek  

 Bu örnek dosyadan okur `test.log`.  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Güçlü programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Satır belirtilen biçim (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>) kullanılarak ayrıştırılamıyor. Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> Özellik satırda bulunan metne atanır.  
  
- Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).  
  
- Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Kullanıcı, dosyaya (<xref:System.UnauthorizedAccessException>) erişmek için yeterli izinlere sahip değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarını Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
