---
title: 'Nasıl: virgülle sınırlandırılmış metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335071"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Nasıl: Visual Basic virgülle sınırlandırılmış metin dosyalarından okuma

Nesne, `TextFieldParser` günlükler gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırmak için bir yol sağlar. Özellik, `TextFieldType` sınırlı bir dosya mı yoksa sabit genişlikte metin alanlarına sahip bir dosya mı olduğunu tanımlar.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Virgül lesınırlı metin dosyasını ayrışdırmak için  
  
1. Yeni `TextFieldParser`bir . Aşağıdaki kod `TextFieldParser` adlandırılmış `MyReader` oluşturur ve `test.txt`dosyayı açar.  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. Türü `TextField` ve sınırlayıcıyı tanımlayın. Aşağıdaki kod `TextFieldType` özelliği """ olarak `Delimited` tanımlar.  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Dosyadaki alanları iletin. Satırlar bozuksa, bir hata bildirin ve ayrıştmaya devam edin. Aşağıdaki kod dosya boyunca döner, her alanı sırayla görüntüler ve yanlış biçimlendirilmiş alanları raporeder.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. `While` Ve `Using` blokları kapatın `End While` `End Using`ve.  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Örnek  

 Bu örnek dosyadan `test.txt`okur.  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Sağlam programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Bir satır belirtilen biçim kullanılarak ayrıştısı olamaz (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi özel durum neden satırı <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> belirtirken, özellik satırda bulunan metin atanır.  
  
- Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Kullanıcının dosyaya erişmek için yeterli izine sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).  
  
- Yol çok uzun<xref:System.IO.PathTooLongException>( ).  
  
- Kullanıcının dosyaya erişmek için yeterli izinleri yoktur (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarını Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
