---
title: 'Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: ee3951e967436a1b8aec09b8e42dc6d1b547bc02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348848"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli Düzendeki Dosyaları Dizine Kopyalama

Yöntem, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> dosyaların yol adlarını temsil eden salt okunur dizeler koleksiyonunu döndürür. `wildCards` Belirli bir desen belirtmek için parametrekullanabilirsiniz.  
  
 Eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.  
  
 Dosyaları bir <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> dizine kopyalamak için yöntemi kullanabilirsiniz.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Belirli bir desene sahip dosyaları bir dizine kopyalamak için  
  
1. Dosya `GetFiles` listesini döndürmek için yöntemi kullanın. Bu örnek, belirtilen dizindeki tüm .rtf dosyalarını döndürür.  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. Dosyaları `CopyFile` kopyalamak için yöntemi kullanın. Bu örnek, dosyaları adlı `testdirectory`dizine kopyalar.  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. İfadeyi `For` bir `Next` deyimle kapatın.  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a>Örnek  

 Yukarıdaki parçacıkları eksiksiz olarak sunan aşağıdaki örnek, belirtilen dizindeki tüm .rtf dosyalarını adlı `testdirectory`dizine kopyalar.  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Dizin yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- Dizin varolan bir dosyayı işaret eder (<xref:System.IO.IOException>).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ). Kullanıcı gerekli izinleri yoksun<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
