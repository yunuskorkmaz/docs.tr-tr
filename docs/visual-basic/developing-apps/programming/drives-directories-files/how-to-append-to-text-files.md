---
title: 'Nasıl Yapılır: Metin Dosyalarına Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348879"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Metin Dosyalarına Ekleme

Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> parametrenin `append` .'a ayarlanmış olduğunu belirterek bir metin `True`dosyasına eklemek için kullanılabilir.  
  
### <a name="to-append-to-a-text-file"></a>Metin dosyasına eklemek için  
  
- Eklenecek `WriteAllText` hedef dosya ve dizeyi belirterek ve `append` parametreyi `True`' ye ayarlayarak yöntemi kullanın.  
  
     Bu örnek, `"This is a test string."` dize adlı `Testfile.txt`dosyaya yazar.  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- `File`olmayan bir yola işaret eder<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>( veya ).  
  
- Dosya başka bir işlem tarafından kullanılıyor veya G/Ç<xref:System.IO.IOException>hatası oluşur ( ).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
