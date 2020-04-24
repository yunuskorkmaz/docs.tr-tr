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

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> Yöntemin aşırı yüklemeleri, bir dizindeki dosyaların adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür:  
  
- Alt dizinleri <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> aramadan, belirtilen dizinde bulunan basit bir dosya araması için aşırı yüklemeyi kullanın.  
  
- Aramanız için <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> ek seçenekler belirtmek üzere aşırı yüklemeyi kullanın. Bir arama kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz. Aramaya alt dizinleri eklemek için `searchType` parametresini olarak <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>ayarlayın.  
  
 Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.  
  
### <a name="to-list-files-in-a-directory"></a>Dizindeki dosyaları listelemek için  
  
- Parametrede arama yapılacak dizinin <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> adını ve yolunu sağlayarak, yöntem aşırı yüklemelerinin birini kullanın. `directory` Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve içine ekler `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.  
  
- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.  
  
- Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
