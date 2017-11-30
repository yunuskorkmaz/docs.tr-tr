---
title: "Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c4549f417e86e82897ca32d8d7cf22aaf462c90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Yöntemi bir dizinde alt dizinler için yol adları temsil eden dizeleri salt okunur bir koleksiyonunu döndürür. Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin. Alt dizinlerinin içeriğini aramasına dahil etmek istiyorsanız, Ayarla `searchType` parametresi `SearchOption.SearchAllSubDirectories`.  
  
 Belirtilen desenle eşleşen hiç dizinleri bulunamazsa, boş bir koleksiyon döndürülür.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir desendeki alt dizinleri bulmak için  
  
-   Kullanım `GetDirectories` yöntemi, aramak istediğiniz dizin konumunu ve adını belirtin. Aşağıdaki örnek, adında "Logs" sözcüğünü içeren tüm dizinleri dizin yapısına döndürür ve eklenmektedir `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Bir veya daha fazla belirtilen joker karakter `Nothing`, boş bir dize veya yalnızca boşluk içeriyor (<xref:System.ArgumentNullException>).  
  
-   `directory`yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory`var olan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [Nasıl yapılır: belirli düzendeki dosyaları bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
