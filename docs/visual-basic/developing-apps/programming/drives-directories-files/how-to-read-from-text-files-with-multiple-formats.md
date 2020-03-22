---
title: 'Nasıl yapılsın: Birden çok biçime sahip metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334578"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>Nasıl yapılsın: Visual Basic'te birden fazla formata sahip fext dosyalarından okuma

Nesne, <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> günlükler gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırmak için bir yol sağlar. Dosyayı `PeekChars` ayrıştirırken her satırın biçimini belirlemek için yöntemi kullanarak birden çok biçime sahip bir dosyayı işleyebilirsiniz.
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Birden çok biçimli bir metin dosyasını ayrışdırmak için

1. Projenize *testfile.txt* adlı bir metin dosyası ekleyin. Metin dosyasına aşağıdaki içeriği ekleyin:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. Bir hata raporlandığında beklenen biçimi ve kullanılan biçimi tanımlayın. Her dizideki son giriş -1'dir, bu nedenle son alanın değişken genişlikte olduğu varsayılır. Bu, dizideki son giriş 0'dan az veya eşit olduğunda oluşur.

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. Genişlik <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> ve biçimi tanımlayan yeni bir nesne oluşturun.

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. Okumadan önce biçim için test, satırlar arasında döngü.

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. Konsola hata yazın.

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>Örnek

Aşağıdaki dosyadan `testfile.txt`okur tam bir örnektir:

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>Sağlam programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Bir satır belirtilen biçim kullanılarak ayrıştısı olamaz (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi özel durum neden satırı <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> belirtirken, özellik satırda bulunan metne atanır.
- Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).
- Kullanıcının dosyaya erişmek için yeterli izine sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).
- Yol çok uzun<xref:System.IO.PathTooLongException>( ).
- Kullanıcının dosyaya erişmek için yeterli izinleri yoktur (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarını Okuma](how-to-read-from-comma-delimited-text-files.md)
- [Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarını Okuma](how-to-read-from-fixed-width-text-files.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](parsing-text-files-with-the-textfieldparser-object.md)
