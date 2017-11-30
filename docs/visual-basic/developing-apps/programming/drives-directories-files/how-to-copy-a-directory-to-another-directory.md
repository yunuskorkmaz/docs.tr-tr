---
title: "Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f20ee767902395439f420f14fc2e352297ad31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama
Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> yöntemi bir dizin başka bir dizine kopyalayın. Bu yöntem, dizini ve bunun yanı sıra dizin içeriğini kopyalar. Hedef dizin yoksa, oluşturulur. Hedef konumda aynı adı taşıyan bir dizin olup olmadığını ve `overwrite` ayarlanır `False`, iki dizin içeriğini birleştirilir. İşlem sırasında dizin için yeni bir ad belirtebilirsiniz.  
  
 Bir dizindeki dosya kopyalarken, özel durumlar neden olduğu birleştirme sırasında var olan bir dosya gibi belirli dosya tarafından durum oluşturulabilir `overwrite` ayarlanır `False`. Bu tür özel durumlar, tek bir özel durum birleştirilir, `Data` özelliği dosya veya dizin yolunu anahtarıdır ve belirli özel durum iletisi içinde karşılık gelen değerle yer alan girişleri içerir.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Bir dizini diğerine kopyalamak için  
  
-   Kullanım `CopyDirectory` yöntemi, kaynak ve hedef dizin adlarını belirtme. Aşağıdaki örnek adlı dizine kopyalar `TestDirectory1` içine `TestDirectory2`, var olan dosyaların üzerine yazılması.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **dosya sistemi - işleme sürücüleri, klasörleri ve dosyaları**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   İki nokta üst üste (:) veya eğik çizgi dizini içeren için belirtilen yeni adı (\ veya /) (<xref:System.ArgumentException>).  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName`olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>)  
  
-   Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Kaynak dizini olan bir kök dizini (<xref:System.IO.IOException>).  
  
-   Birleşik yolu varolan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Kaynak yolu ve hedef yolu aynıdır (<xref:System.IO.IOException>).  
  
-   `ShowUI`ayarlanmış `UIOption.AllDialogs` ve kullanıcı işlemi iptal ya da dizindeki bir veya daha fazla dosya kopyalanamıyor (<xref:System.OperationCanceledException>).  
  
-   Döngüsel bir işlemdir (<xref:System.InvalidOperationException>).  
  
-   Yol, iki nokta üst üste (:) içeriyor. (<xref:System.NotSupportedException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Bir hedef dosya varsa, ancak erişilemiyor (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>  
 [Nasıl yapılır: belirli bir desendeki alt dizinleri bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Nasıl yapılır: bir dizindeki dosya koleksiyonunu alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
