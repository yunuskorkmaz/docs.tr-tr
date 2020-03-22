---
title: 'Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bb07ae25b413334f94456b378f0a2339402ac668
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335331"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> Yöntemin aşırı yükleri, dizindeki dosyaların adlarını temsil eden salt okunur dizeler koleksiyonunu döndürer:  
  
- Alt <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> dizinlerde arama yapmadan, belirli bir dizinde basit bir dosya araması için aşırı yüklemeyi kullanın.  
  
- Aramanız <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> için ek seçenekler belirtmek için aşırı yüklemeyi kullanın. `wildCards` Bir arama deseni belirtmek için parametreyi kullanabilirsiniz. Alt dizinleri aramaya eklemek için `searchType` parametreyi ' ye <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>ayarlar  
  
 Belirtilen desenle eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.  
  
### <a name="to-list-files-in-a-directory"></a>Dizindeki dosyaları listelemek için  
  
- `directory` Parametrede <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> arama yapmak için dizinin adını ve yolunu sağlayarak yöntemin aşırı yüklerinden birini kullanın. Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve `ListBox1`ekler.  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory`varolan bir dosyaya işaret eder (<xref:System.IO.IOException>).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
- Kullanıcı gerekli izinleri yoksun<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
