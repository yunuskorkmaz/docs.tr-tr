---
title: 'Nasıl yapılır: Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f95a0c4df4a2eab0069a6dab0d4c3fa338d1d8ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411544"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosyalara Metin Yazma

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Yöntemi, dosyalara metin yazmak için kullanılabilir. Belirtilen dosya yoksa, oluşturulur.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-text-to-a-file"></a>Bir dosyaya metin yazmak için  
  
- `WriteAllText`Bir dosyaya metin yazmak için yöntemini kullanın, yazılacak dosyayı ve metni belirtin. Bu örnek `"This is new text."` `test.txt` , metni dosyasındaki varolan metne ekleyerek satırı adlı dosyaya yazar.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Bir dosyaya bir dizi dize yazmak için  
  
- Dize koleksiyonu aracılığıyla döngü yapın. `WriteAllText`Eklenecek hedef dosyayı ve dizeyi belirterek bir dosyaya metin yazmak için yöntemini kullanın `append` `True` .  
  
     Bu örnek, dizinde bulunan dosyaların adlarını `Documents and Settings` `FileList.txt` , daha iyi okunabilirlik için her biri arasına bir satır başı ekleyerek yazar.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- `File`varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).  
  
- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
- Disk dolu ve `WriteAllText` () çağrısı başarısız olur <xref:System.IO.IOException> .  
  
 Kısmi güven bağlamında çalıştırıyorsanız, yetersiz ayrıcalıklar nedeniyle kod bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Nasıl yapılır: metin dosyalarından okuma](how-to-read-from-text-files.md)
