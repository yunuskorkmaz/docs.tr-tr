---
title: "Nasıl yapılır: Visual Basic'te ikili dosyalara yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 9e83029b7b5fd635ff08e608760b6c64c7945da0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965936"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te ikili dosyalara yazma
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Yöntemi veri bir ikili dosyaya yazar. Varsa `append` parametresi `True`, dosyaya veri ekler; Aksi takdirde dosyasındaki verilerin üzerine yazılır.  
  
 Dosya adı hariç belirtilen yol geçerli değilse bir <xref:System.IO.DirectoryNotFoundException> özel durumu oluşturulur. Yolun geçerli olduğundan, ancak dosya yok, dosya oluşturulur.  
  
### <a name="to-write-to-a-binary-file"></a>Bir ikili dosyaya yazmak için  
  
-   Kullanım `WriteAllBytes` dosya yolu ve adı ile yazılacak baytları sağlama yöntemi. Bu örnek veri dizisi ekler `CustomerData` adlı dosyaya `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir durum oluşturabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize; olan Bu, yalnızca boşluk içermektedir; veya geçersiz karakterler içeriyor. (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` mevcut olmayan bir yola işaret (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).  
  
-   Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Nasıl yapılır: Dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
