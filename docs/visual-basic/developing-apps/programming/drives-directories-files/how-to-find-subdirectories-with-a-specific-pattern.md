---
title: "Nasıl yapılır: Visual Basic'te belirli bir desendeki alt dizinleri bulma"
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 705fa6e40d0e6d18826966e3f10cfd31d9e7a6ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823408"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te belirli bir desendeki alt dizinleri bulma
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Yöntemi bir dizinde bir alt dizinler için yol adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür. Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin. Alt dizinlerinin içeriğini aramaya dahil etmek istediğiniz verilirse `searchType` parametresi `SearchOption.SearchAllSubDirectories`.  
  
 Belirtilen desenle eşleşen bir dizin yok bulunamazsa boş bir koleksiyon döndürülür.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir desendeki alt dizinleri bulmak için  
  
-   Kullanım `GetDirectories` yöntemi, aramak istediğiniz dizinin yolunu ve adını belirtin. Aşağıdaki örnek, dizin yapısına sözcüğünü içeren tüm dizinler "Logs" adında döndürür ve eklenmeye `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Bir veya daha fazla belirtilen joker karakter `Nothing`, boş bir dize veya yalnızca boşluk içeriyor (<xref:System.ArgumentNullException>).  
  
-   `directory` yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` Varolan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl yapılır: Belirli bir düzendeki dosyaları bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
