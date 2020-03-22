---
title: 'Nasıl Yapılır: Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334468"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosyalara Metin Yazma

Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> dosyalara metin yazmak için kullanılabilir. Belirtilen dosya yoksa, oluşturulur.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-text-to-a-file"></a>Dosyaya metin yazmak için  
  
- Dosyaya `WriteAllText` metin yazmak için, dosyayı ve yazılacak metni belirtmek için yöntemi kullanın. Bu örnek, `"This is new text."` satırı dosyadaki `test.txt`varolan herhangi bir metne ekolarak, adlı dosyaya yazar.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Bir dosyaya bir dizi dize yazmak için  
  
- Dize koleksiyonu üzerinden döngü. Dosyaya `WriteAllText` metin yazmak, eklenecek hedef dosya ve dizeyi belirtmek `append` ve `True`''e ayar yapmak için yöntemi kullanın.  
  
     Bu örnek, daha iyi okunabilirlik için `FileList.txt`her biri arasında bir satır başı eklemek için `Documents and Settings` dizindeki dosyaların adlarını yazar.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- `File`olmayan bir yola işaret eder<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>( veya ).  
  
- Dosya başka bir işlem tarafından kullanılıyor veya G/Ç<xref:System.IO.IOException>hatası oluşur ( ).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
- Disk dolu ve çağrı `WriteAllText` başarısız olur<xref:System.IO.IOException>( ).  
  
 Kısmi güven bağlamında çalışıyorsanız, kod yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir. Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Nasıl Yapılsın: Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
