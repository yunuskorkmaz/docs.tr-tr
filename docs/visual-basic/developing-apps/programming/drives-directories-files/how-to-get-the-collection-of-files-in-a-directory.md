---
title: "Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c9245ab2593dfed5201640ecf84713582890334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma
Aşırı <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntemi bir dizini içindeki dosyaların adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür:  
  
-   Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> basit dosya arama alt dizinleri arama olmadan belirtilen bir dizinde için aşırı yükleme.  
  
-   Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> aşırı aramanız için ek seçenekleri belirtin. Kullanabileceğiniz `wildCards` parametresini kullanarak bir arama deseni belirtin. Arama alt dizinleri içerecek şekilde `searchType` parametresi <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Belirtilen desenle eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.  
  
### <a name="to-list-files-in-a-directory"></a>Bir dizindeki dosyaları listelemek için  
  
-   Aşağıdakilerden birini kullanmak <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntemi aşırı yüklemeleri, içinde arama yapmak istediğiniz dizinin yolu ve adı sağladığını `directory` parametresi. Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve eklenmektedir `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory`yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory`var olan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [Nasıl yapılır: belirli düzendeki dosyaları bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [Nasıl yapılır: belirli bir desendeki alt dizinleri bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
