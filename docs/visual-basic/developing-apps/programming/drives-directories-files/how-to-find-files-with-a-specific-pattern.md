---
title: 'Nasıl yapılır: Belirli bir Düzendeki Dosyaları Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 71073672ed14cb2d5df5b5365266b718c59cb18f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401647"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Düzendeki Dosyaları Bulma

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. `wildCards`Belirli bir kalıbı belirtmek için parametresini kullanabilirsiniz. Aramaya alt dizinler eklemek isterseniz, `searchType` parametresini olarak ayarlayın `SearchOption.SearchAllSubDirectories` .  
  
 Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.  
  
> [!NOTE]
> Ad alanının sınıfını kullanarak bir dosya listesi döndürme hakkında daha fazla bilgi için `DirectoryInfo` `System.IO` bkz <xref:System.IO.DirectoryInfo.GetFiles%2A> ..  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Belirtilen bir düzene sahip dosyaları bulmak için  
  
- `GetFiles`Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve modelini belirterek yöntemini kullanın. Aşağıdaki örnek, dizininde uzantısı olan tüm dosyaları döndürür `.dll` ve içine ekler `ListBox1` .  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- `directory`yok ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- `directory`var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
- Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma](how-to-get-the-collection-of-files-in-a-directory.md)
