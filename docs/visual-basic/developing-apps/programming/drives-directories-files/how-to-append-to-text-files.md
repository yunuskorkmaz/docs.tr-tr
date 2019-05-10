---
title: "Nasıl yapılır: Visual Basic'te metin dosyalarına ekleme"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: e855293ac3636049520a85abdf685091d437bb60
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628901"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te metin dosyalarına ekleme
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Belirterek bir metin dosyasına eklenecek yöntemi kullanılabilir `append` parametrenin ayarlanmış `True`.  
  
### <a name="to-append-to-a-text-file"></a>Bir metin dosyasına eklemek için  
  
- Kullanım `WriteAllText` yöntemi, eklenecek dizeyi ve hedef dosya belirtme ve ayarı `append` parametresi `True`.  
  
     Bu örnek bir dize Yazar `"This is a test string."` adlı dosyaya `Testfile.txt`.  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
- `File` mevcut olmayan bir yola işaret (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).  
  
- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).  
  
- Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
- Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
