---
title: 'Nasıl: sabit genişlikte metin Dosyaları okuma'
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
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Nasıl: Visual Basic'teki sabit genişlikteki metin dosyalarından okuma

Nesne, `TextFieldParser` günlükler gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırmak için bir yol sağlar.  
  
 Özellik, `TextFieldType` ayrıştırılan dosyanın sınırlı bir dosya mı yoksa sabit genişlikte metin alanlarına sahip bir dosya mı olduğunu tanımlar. Sabit genişlikteki metin dosyasında, sonundaki alan değişken genişliğe sahip olabilir. Sonundaki alanın değişken genişliği olduğunu belirtmek için, genişliği sıfırdan küçük veya eşit olacak şekilde tanımlayın.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Sabit genişlikte metin dosyasını ayrışdırmak için  
  
1. Yeni `TextFieldParser`bir . Aşağıdaki kod `TextFieldParser` adlandırılmış `Reader` oluşturur ve `test.log`dosyayı açar.  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. `TextFieldType` Özelliği, genişlik ve biçimi tanımlayan olarak `FixedWidth`tanımlayın. Aşağıdaki kod metin sütunlarını tanımlar; birincisi 5 karakter genişliğinde, ikincisi 10, üçüncü 11 ve dördüncü değişken genişliktedir.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Dosyadaki alanları iletin. Satırlar bozuksa, bir hata bildirin ve ayrıştmaya devam edin.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. `While` Ve `Using` blokları kapatın `End While` `End Using`ve.  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Örnek  

 Bu örnek dosyadan `test.log`okur.  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Sağlam programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Bir satır belirtilen biçim kullanılarak ayrıştısı olamaz (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi özel durum neden satırı <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> belirtirken, özellik satırda bulunan metne atanır.  
  
- Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Kullanıcının dosyaya erişmek için yeterli izine sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).  
  
- Yol çok uzun<xref:System.IO.PathTooLongException>( ).  
  
- Kullanıcının dosyaya erişmek için yeterli izinleri yoktur (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarını Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
