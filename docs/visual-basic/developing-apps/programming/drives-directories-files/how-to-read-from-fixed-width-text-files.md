---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic sabit genişlikli metin dosyalarından okuma'
title: 'Nasıl yapılır: sabit genişlikli metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 4f5868fa68009851cc65eeaf5ff6431ac22840d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797464"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic içindeki sabit genişlikli metin dosyalarından okuma

`TextFieldParser`Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.  
  
 `TextFieldType`Özelliği, ayrıştırılmış dosyanın ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları olduğunu tanımlar. Sabit genişlikli bir metin dosyasında, sonundaki alanın bir değişken genişliği olabilir. Uçtaki alanın bir değişken genişliğine sahip olduğunu belirtmek için, bu değeri sıfıra eşit veya daha küçük bir genişliğe sahip olacak şekilde tanımlayın.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Sabit genişlikli bir metin dosyasını ayrıştırmak için  
  
1. Yeni bir oluştur `TextFieldParser` . Aşağıdaki kod, `TextFieldParser` adlı adı oluşturur `Reader` ve dosyasını açar `test.log` .  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Özelliği, `TextFieldType` `FixedWidth` genişliği ve biçimi tanımlayarak tanımlayın. Aşağıdaki kod, metnin sütunlarını tanımlar; Birincisi 5 karakter genişliğinde, ikinci 10, üçüncü 11 ve dördüncü değişken genişliktedir.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Dosyadaki alanlar arasında döngü gerçekleştirin. Herhangi bir satır bozuksa, bir hata bildirin ve ayrıştırmaya devam edin.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Ve `While` `Using` bloklarıyla birlikte kapatın `End While` `End Using` .  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Örnek  

 Bu örnek dosyadan okur `test.log` .  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Güçlü programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Satır belirtilen biçim () kullanılarak ayrıştırılamıyor <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> . Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özellik satırda bulunan metne atanır.  
  
- Belirtilen dosya yok ( <xref:System.IO.FileNotFoundException> ).  
  
- Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).  
  
- Yol çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
- Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](how-to-read-from-comma-delimited-text-files.md)
- [Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](walkthrough-manipulating-files-and-directories.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](troubleshooting-reading-from-and-writing-to-text-files.md)
