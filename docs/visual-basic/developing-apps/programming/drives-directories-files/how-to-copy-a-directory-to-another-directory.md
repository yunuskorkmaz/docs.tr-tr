---
title: "Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 9b6e095d061619cf9d2e2d87a7247cbdbc51cbe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
-   `destinationDirectoryName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>)  
  
-   Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Kaynak dizini olan bir kök dizini (<xref:System.IO.IOException>).  
  
-   Birleşik yolu varolan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
-   Kaynak yolu ve hedef yolu aynıdır (<xref:System.IO.IOException>).  
  
-   `ShowUI` ayarlanmış `UIOption.AllDialogs` ve kullanıcı işlemi iptal ya da dizindeki bir veya daha fazla dosya kopyalanamıyor (<xref:System.OperationCanceledException>).  
  
-   Döngüsel bir işlemdir (<xref:System.InvalidOperationException>).  
  
-   Yol, iki nokta üst üste (:) içeriyor. (<xref:System.NotSupportedException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Bir hedef dosya varsa, ancak erişilemiyor (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>  
 [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
