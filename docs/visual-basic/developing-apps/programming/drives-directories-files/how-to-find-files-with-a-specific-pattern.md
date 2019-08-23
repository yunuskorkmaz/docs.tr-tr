---
title: 'Nasıl yapılır: Visual Basic belirli bir düzene sahip dosyaları bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: f35222d958f8b02f83c6575d940d24e359c3ae00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914725"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Nasıl yapılır: Visual Basic belirli bir düzene sahip dosyaları bulma
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. Belirli bir kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz. Aramaya alt dizinler eklemek isterseniz, `searchType` parametresini olarak `SearchOption.SearchAllSubDirectories`ayarlayın.  
  
 Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.  
  
> [!NOTE]
> `System.IO` Ad alanının `DirectoryInfo` sınıfını kullanarak bir dosya listesi döndürme hakkında daha fazla bilgi için bkz <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Belirtilen bir düzene sahip dosyaları bulmak için  
  
- Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve modelini belirterek yönteminikullanın.`GetFiles` Aşağıdaki örnek, dizininde uzantısı `.dll` olan tüm dosyaları döndürür ve içine ekler. `ListBox1`  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.  
  
- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.  
  
- Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl yapılır: Belirli bir düzene sahip alt dizinler bulun](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun giderme: Metin dosyalarından okuma ve yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl yapılır: Dizindeki dosyaların toplanmasını al](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
