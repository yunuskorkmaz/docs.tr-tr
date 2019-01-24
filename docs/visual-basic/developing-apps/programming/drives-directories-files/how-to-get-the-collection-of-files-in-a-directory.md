---
title: "Nasıl yapılır: Visual Basic'te bir dizindeki dosya koleksiyonunu alma"
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: a708d9cfd7b1a5ded3088ee567660bd0b3a5423f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731939"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te bir dizindeki dosya koleksiyonunu alma
Aşırı Yüklemeleri <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntem dizindeki dosyaların adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür:  
  
-   Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> belirtilen bir dizinde arama alt dizinleri olmadan, bir basit dosya arama için aşırı yükleme.  
  
-   Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> aramanız için ek seçenekleri belirlemek için aşırı yükleme. Kullanabileceğiniz `wildCards` parametresini kullanarak arama deseni belirtin. Alt dizinler aramaya dahil etmek için ayarlama `searchType` parametresi <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Belirtilen desenle eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.  
  
### <a name="to-list-files-in-a-directory"></a>Bir dizindeki dosyaları listelemek için  
  
-   Birini <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntemi aşırı yüklemeleri, içinde arama yapılacak dizinin yolunu ve adını sağlama `directory` parametresi. Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve eklenmeye `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory` yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` Varolan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Nasıl yapılır: Belirli bir düzendeki dosyaları bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
