---
title: LINQ ve Dosya Dizinleri
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 390d3c7a1c738aea0df8e3dcad0edb70563f8fb6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347794"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ ve dosya dizinleri (Visual Basic)
Birçok dosya sistemi işlemi aslında sorgular ve bu nedenle LINQ yaklaşımına uygundur.  
  
 Bu bölümdeki sorguların bozucu olmadığına unutmayın. Özgün dosyaların veya klasörlerin içeriğini değiştirmek için kullanılmaz. Bu, sorguların hiçbir yan etkiye neden olmaması gerektiğine yönelik kuralı izler. Genel olarak, kaynak verileri değiştiren tüm kodlar (oluşturma/güncelleştirme/silme işleçleri de dahil olmak üzere) yalnızca verileri sorgulayan koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <xref:System.IO.FileInfo> nesnesinin bir veya daha fazla özelliğini inceleyerek dosyaların nasıl aranacağını gösterir.  
  
 [Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 <xref:System.IO.FileInfo> nesne gruplarının dosya adı uzantısına göre nasıl geri alınacağını gösterir.  
  
 [Nasıl yapılır: bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Belirtilen bir dizin ağacındaki tüm dosyalardaki toplam bayt sayısının nasıl geri yükleneceğini gösterir.  
  
 [Nasıl yapılır: Iki klasörün Içeriğini karşılaştırma (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Belirtilen iki klasörde bulunan tüm dosyaları ve aynı zamanda bir klasörde bulunan ancak diğeri olmayan tüm dosyaları döndürmeyi gösterir.  
  
 [Nasıl yapılır: bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Bir dizin ağacında en büyük veya en küçük dosyanın veya belirli bir sayıdaki dosyanın nasıl döndürülmeli olduğunu gösterir.  
  
 [Nasıl yapılır: bir dizin ağacında (LINQ) yinelenen dosyalar için sorgu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen bir dizin ağacındaki birden fazla konumda gerçekleşen tüm dosya adlarının nasıl gruplandıralınacağını gösterir. Ayrıca, özel bir karşılaştırıcıyı temel alan daha karmaşık karşılaştırmalar yapmayı gösterir.  
  
 [Bir klasördeki dosyaların içeriğini sorgulama (LINQ) (Visual Basic)](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Bir ağaçtaki klasörlerin nasıl tekrarlanması, her dosyanın nasıl açılacağı ve dosyanın içeriğini sorgulama işlemlerinin nasıl yapılacağını gösterir.  
  
## <a name="comments"></a>Açıklamalar  
 Dosya sisteminin içeriğini doğru bir şekilde temsil eden bir veri kaynağı oluşturma konusunda bazı karmaşıklıklar vardır ve özel durumları düzgün bir şekilde işler. Bu bölümdeki örneklerde, belirtilen bir kök klasörü ve tüm alt klasörleri altındaki tüm dosyaları temsil eden <xref:System.IO.FileInfo> nesnelerinin bir anlık görüntü koleksiyonu oluşturulur. Her bir <xref:System.IO.FileInfo> gerçek durumu, bir sorgu yürütme ve sonlandırma arasındaki sürede değişebilir. Örneğin, bir veri kaynağı olarak kullanmak üzere <xref:System.IO.FileInfo> nesnelerinin bir listesini oluşturabilirsiniz. Bir sorgudaki `Length` özelliğine erişmeyi denerseniz, <xref:System.IO.FileInfo> nesnesi `Length`değerini güncelleştirmek için dosya sistemine erişmeye çalışır. Dosya artık yoksa, dosya sistemini doğrudan sorguladığınız halde sorgunuzda bir <xref:System.IO.FileNotFoundException> alırsınız. Bu bölümdeki bazı sorgular belirli durumlarda bu özel durumları tüketen ayrı bir yöntem kullanır. Diğer bir seçenek de <xref:System.IO.FileSystemWatcher>kullanarak veri kaynağınızı dinamik olarak güncel tutkullanmaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
