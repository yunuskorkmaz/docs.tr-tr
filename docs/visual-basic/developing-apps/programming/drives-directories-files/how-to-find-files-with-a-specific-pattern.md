---
title: 'Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348753"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Düzendeki Dosyaları Bulma

Yöntem, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> dosyaların yol adlarını temsil eden salt okunur dizeler koleksiyonunu döndürür. `wildCards` Belirli bir desen belirtmek için parametrekullanabilirsiniz. Alt dizinleri aramaya eklemek istiyorsanız, parametreyi `searchType` ' `SearchOption.SearchAllSubDirectories`ye ayarlarsınız.  
  
 Belirtilen desenle eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.  
  
> [!NOTE]
> Ad `DirectoryInfo` alanının sınıfını kullanarak dosya listesini döndürme hakkında bilgi için bkz. <xref:System.IO.DirectoryInfo.GetFiles%2A> `System.IO`  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Belirli bir desene sahip dosyaları bulmak için  
  
- Arama `GetFiles` yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve deseni belirterek yöntemi kullanın. Aşağıdaki örnek, dizindeki uzantılı `.dll` tüm dosyaları döndürür ve `ListBox1`ekler.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory`varolan bir dosyaya işaret eder (<xref:System.IO.IOException>).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
- Kullanıcı gerekli izinleri yoksun<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
