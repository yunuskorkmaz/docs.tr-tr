---
title: 'Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401621"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma

Yöntemin aşırı yüklemeleri, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> bir dizindeki dosyaların adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür:  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29>Alt dizinleri aramadan, belirtilen dizinde bulunan basit bir dosya araması için aşırı yüklemeyi kullanın.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])>Aramanız için ek seçenekler belirtmek üzere aşırı yüklemeyi kullanın. `wildCards`Bir arama kalıbı belirtmek için parametresini kullanabilirsiniz. Aramaya alt dizinleri eklemek için `searchType` parametresini olarak ayarlayın <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType> .  
  
 Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.  
  
### <a name="to-list-files-in-a-directory"></a>Dizindeki dosyaları listelemek için  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType>Parametrede arama yapılacak dizinin adını ve yolunu sağlayarak, yöntem aşırı yüklemelerinin birini kullanın `directory` . Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve içine ekler `ListBox1` .  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- `directory`yok ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- `directory`var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
- Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Nasıl yapılır: Belirli bir Düzendeki Dosyaları Bulma](how-to-find-files-with-a-specific-pattern.md)
- [Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](how-to-find-subdirectories-with-a-specific-pattern.md)
