---
title: 'Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348753"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Düzendeki Dosyaları Bulma

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. Belirli bir kalıbı belirtmek için `wildCards` parametresini kullanabilirsiniz. Aramaya alt dizinler eklemek isterseniz, `searchType` parametresini `SearchOption.SearchAllSubDirectories`olarak ayarlayın.  
  
 Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.  
  
> [!NOTE]
> `System.IO` ad alanının `DirectoryInfo` sınıfını kullanarak bir dosya listesi döndürme hakkında daha fazla bilgi için bkz. <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Belirtilen bir düzene sahip dosyaları bulmak için  
  
- Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve modelini belirterek `GetFiles` yöntemini kullanın. Aşağıdaki örnek, dizinde `.dll` uzantısı olan tüm dosyaları döndürür ve `ListBox1`ekler.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.  
  
- `directory` yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
- Kullanıcının gerekli izinleri yok (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
