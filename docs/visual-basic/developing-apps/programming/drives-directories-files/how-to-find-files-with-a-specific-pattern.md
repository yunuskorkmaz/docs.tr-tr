---
title: "Nasıl yapılır: Visual Basic'te belirli düzendeki dosyaları bulma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 879f7a2335e3c4c31b0a7ddd3d303486d8b95a22
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970473"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te belirli düzendeki dosyaları bulma
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Yöntemi dosyaları için yol adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür. Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin. Alt dizinler aramaya dahil etmek istediğiniz verilirse `searchType` parametresi `SearchOption.SearchAllSubDirectories`.  
  
 Belirtilen desenle eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.  
  
> [!NOTE]
>  Dosya listesi kullanarak döndürme hakkında bilgi için `DirectoryInfo` sınıfının `System.IO` ad bkz <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Belirli bir düzendeki dosyaları bulmak için  
  
-   Kullanım `GetFiles` aramak istediğiniz dizinin yolunu ve adını sağlayan ve düzeni belirtme yöntemi. Aşağıdaki örnek uzantılı tüm dosyaları döndürür `.dll` dizinde eklenmeye ve `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory` yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` Varolan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun giderme: Okuma ve dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
