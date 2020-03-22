---
title: 'Nasıl Yapılır: İkili Dosyaları Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: c33bc72a5c79901e3715ed6a587ffdb8e3565e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335289"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te İkili Dosyaları Okuma

Nesne `My.Computer.FileSystem` ikili `ReadAllBytes` dosyalardan okuma yöntemini sağlar.  
  
### <a name="to-read-from-a-binary-file"></a>İkili dosyadan okumak için  
  
- Bir `ReadAllBytes` dosyanın içeriğini bayt dizisi olarak döndüren yöntemi kullanın. Bu örnek dosyadan `C:/Documents and Settings/selfportrait.jpg`okur.  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- Büyük ikili dosyalar için, <xref:System.IO.FileStream.Read%2A> <xref:System.IO.FileStream> dosyadan yalnızca belirli bir miktarı aynı anda okumak için nesnenin yöntemini kullanabilirsiniz. Daha sonra, her okuma işlemi için dosyanın ne kadarının belleğe yüklendiğini sınırlayabilirsiniz. Aşağıdaki kod örneği bir dosyayı kopyalar ve arayanın dosyanın okuma işlemi başına belleğe ne kadarının okunduğunu belirtmesine olanak tanır.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durum atılmasına neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunlukta bir dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, ya da bir aygıt yolu ( ).<xref:System.ArgumentException>  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Dosya başka bir işlem tarafından kullanılıyor veya G/Ç<xref:System.IO.IOException>hatası oluşur ( ).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Arabellek için dize yazmak için yeterli<xref:System.OutOfMemoryException>bellek yoktur ( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası Visual Basic kaynak dosyası olmayabilir.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Verileri Panoda Depolama ve Panodan Okuma](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
