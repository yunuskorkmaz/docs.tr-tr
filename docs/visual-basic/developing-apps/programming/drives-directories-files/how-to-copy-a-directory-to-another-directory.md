---
title: "Nasıl yapılır: Başka bir dizine Visual Basic'te bir dizini kopyalama"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 9a02407ea805db4ae23f001de49ed6610f807b8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628879"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Nasıl yapılır: Başka bir dizine Visual Basic'te bir dizini kopyalama
Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> başka bir dizini kopyalama için yöntemi. Bu yöntem, dizini ve bunun yanı sıra dizin içeriğini kopyalar. Hedef dizin yoksa, oluşturulur. Hedef konumda aynı adda bir dizin olup olmadığını ve `overwrite` ayarlanır `False`, iki dizin içeriğini birleştirilir. İşlem sırasında dizini için yeni bir ad belirtebilirsiniz.  
  
 Dizindeki dosyaları kopyalarken, özel durumların neden olduğu birleştirme sırasında var olan bir dosya gibi belirli dosya tarafından oluşturulabilir `overwrite` ayarlanır `False`. Bu tür özel durumlar oluşturulduğunda, tek bir özel durum birleştirilir, `Data` anahtar dosya veya dizin yoludur ve karşılık gelen değer belirli bir özel durum iletisi yer alan girişleri özelliği içerir.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Bir dizini diğerine kopyalama için  
  
- Kullanım `CopyDirectory` yöntemi, kaynak ve hedef dizin adlarını belirleme. Aşağıdaki örnekte adlı dizine kopyalanır `TestDirectory1` içine `TestDirectory2`, mevcut dosyaların üzerine.  
  
     [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]  
  
     Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **dosya sistemi - işleme sürücüler, klasörler ve dosyaları**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dizin bir iki nokta üst üste (:) veya eğik çizgi içeriyor. belirtilen yeni adı (\ veya /) (<xref:System.ArgumentException>).  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
- `destinationDirectoryName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>)  
  
- Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).  
  
- Kaynak dizini kök dizindir (<xref:System.IO.IOException>).  
  
- Birleşik yolu varolan bir dosyaya işaret (<xref:System.IO.IOException>).  
  
- Kaynak yolu ve hedef yolu aynıdır (<xref:System.IO.IOException>).  
  
- `ShowUI` ayarlanır `UIOption.AllDialogs` ve kullanıcı işlemi iptal ya da bir veya daha fazla dosyalarını şu dizinde kopyalanamaz (<xref:System.OperationCanceledException>).  
  
- Döngüsel bir işlemdir (<xref:System.InvalidOperationException>).  
  
- Yol, iki nokta üst üste (:) içeriyor. (<xref:System.NotSupportedException>).  
  
- Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
- Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
- Bir hedef dosya var, ancak erişilemez (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
