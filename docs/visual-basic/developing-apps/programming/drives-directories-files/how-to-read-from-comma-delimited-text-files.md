---
title: 'Nasıl yapılır: virgülle ayrılmış metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411648"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic içinde virgülle ayrılmış metin dosyalarından okuma

`TextFieldParser`Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar. `TextFieldType`Özelliği, bunun ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları mı olduğunu tanımlar.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Virgülle ayrılmış bir metin dosyasını ayrıştırmak için  
  
1. Yeni bir oluştur `TextFieldParser` . Aşağıdaki kod, `TextFieldParser` adlı adı oluşturur `MyReader` ve dosyasını açar `test.txt` .  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. `TextField`Türü ve sınırlandırıcıyı tanımlayın. Aşağıdaki kod, `TextFieldType` `Delimited` "," olarak özelliği ve sınırlandırıcıyı tanımlar.  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Dosyadaki alanlar arasında döngü gerçekleştirin. Herhangi bir satır bozuksa bir hata bildirin ve ayrıştırmaya devam edin. Aşağıdaki kod, dosyasında her bir alanı görüntüleyerek ve yanlış biçimlendirilmiş tüm alanları bildiren bir dosya üzerinden döngü başlatır.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. Ve `While` `Using` bloklarıyla birlikte kapatın `End While` `End Using` .  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Örnek  

 Bu örnek dosyadan okur `test.txt` .  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Güçlü programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Satır belirtilen biçim () kullanılarak ayrıştırılamıyor <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> . Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliğe satırda içerilen metin atanır.  
  
- Belirtilen dosya yok ( <xref:System.IO.FileNotFoundException> ).  
  
- Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).  
  
- Yol çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
- Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma](how-to-read-from-fixed-width-text-files.md)
- [Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](walkthrough-manipulating-files-and-directories.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](troubleshooting-reading-from-and-writing-to-text-files.md)
