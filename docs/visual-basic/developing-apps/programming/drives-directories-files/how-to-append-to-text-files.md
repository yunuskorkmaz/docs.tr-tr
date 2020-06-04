---
title: 'Nasıl yapılır: Metin Dosyalarına Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 53b2e4c9030e9d1dd81a4121ad3f92aad796e3e1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359961"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Metin Dosyalarına Ekleme

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Yöntemi, parametresinin olarak ayarlandığını belirterek bir metin dosyasına eklemek için kullanılabilir `append` `True` .  
  
### <a name="to-append-to-a-text-file"></a>Bir metin dosyasına eklemek için  
  
- `WriteAllText`Eklenecek hedef dosyayı ve dizeyi belirterek ve parametresini olarak ayarlamak için yöntemini kullanın `append` `True` .  
  
     Bu örnek, dizeyi `"This is a test string."` adlı dosyaya yazar `Testfile.txt` .  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- `File`varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).  
  
- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Dosyalara Yazma](writing-to-files.md)
