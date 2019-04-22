---
title: "Nasıl yapılır: Visual Basic'te ikili dosyaları okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 88c9952818f6cb94db7b2da7ad44aa0da0eb43d2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825059"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te ikili dosyaları okuma
`My.Computer.FileSystem` Nesnesi sağlar `ReadAllBytes` ikili dosyaları okuma için yöntemi.  
  
### <a name="to-read-from-a-binary-file"></a>İkili dosyasından okunamıyor  
  
-   Kullanım `ReadAllBytes` yöntemi bir bayt dizisi olarak bir dosyanın içeriğini döndürür. Bu örnekte dosyadan okur `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
-   Büyük ikili dosyalar için kullandığınız <xref:System.IO.FileStream.Read%2A> yöntemi <xref:System.IO.FileStream> dosyasından belirtilen bir miktarı bir kerede okumak için nesne. Ardından, dosyanın ne kadar her okuma işlemi için belleğe yüklenen sınırlayabilirsiniz. Aşağıdaki kod örneği, bir dosyayı kopyalar ve ne kadar dosya okuma işlemi başına belleğe okunur belirtmek çağıranın izin verir.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar, bir özel durum oluşturulmasına neden:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Dizeyi arabelleğe yazmak için yeterli bellek yok (<xref:System.OutOfMemoryException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Verileri Panoda Depolama ve Panodan Okuma](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
