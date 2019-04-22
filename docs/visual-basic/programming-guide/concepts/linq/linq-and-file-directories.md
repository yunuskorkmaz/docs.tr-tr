---
title: LINQ ve dosya dizinleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 56967a82bf63d8421d34af48dcc6384ded85e2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825124"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ ve dosya dizinleri (Visual Basic)
Çok sayıda dosya sistemi işlemleri temelde sorgular ve bu nedenle LINQ yaklaşım için çok uygundur.  
  
 Bu bölümdeki sorguların bozucu olmayan olduğunu unutmayın. Özgün dosya ve klasörlerin içeriğini değiştirmek için kullanılmaz. Bu sorgu tüm yan etkileri oluşmamalıdır kuralı izler. Genel olarak, kaynak verileri değiştiren (gerçekleştirmek de dahil olmak üzere sorguları oluşturma / güncelleştirme / delete işleçleri) herhangi bir kod yalnızca verileri sorgular koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: Belirli bir öznitelik veya ada (Visual Basic) sahip dosyaları sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Bir veya daha fazla özelliklerini inceleyerek dosyalarının aranacağı gösterilmektedir, <xref:System.IO.FileInfo> nesne.  
  
 [Nasıl yapılır: Grup dosyalarını uzantısı (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Grupları döndürülecek gösterilmektedir <xref:System.IO.FileInfo> nesne dosya adı uzantılarına bağlı.  
  
 [Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Toplam bayt sayısı belirtilen dizin ağacındaki tüm dosyaları döndürmek gösterilmektedir.  
  
 [Nasıl yapılır: İki klasör (LINQ) (Visual Basic) içeriğini karşılaştırma](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Belirtilen iki klasörlerinde bulunan tüm dosyaları ve bir klasör ancak diğer mevcut olan ayrıca tüm dosyaları iade işlemi gösterilmektedir.  
  
 [Nasıl yapılır: En büyük dosya veya dizin ağacında (LINQ) (Visual Basic) dosyalar için sorgu](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Nasıl bir dizin ağacındaki en büyük veya en küçük dosya veya dosyalar, belirtilen sayıda döndürüleceğini gösterir.  
  
 [Nasıl yapılır: Sorgu (LINQ) (Visual Basic) bir dizin ağacında yineleyen dosyalar için](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen dizin ağacı birden fazla konumda gerçekleşen tüm dosya adları için gruplandırma işlemi gösterilmektedir. Ayrıca özel bir karşılaştırıcı üzerinde dayalı daha karmaşık karşılaştırmalar yapmak nasıl gösterir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) bir klasördeki dosyaların içeriğini sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Bir ağaç klasörlerinde yinelemek, her dosyasını açın ve dosyanın içeriğini sorgu işlemi gösterilmektedir.  
  
## <a name="comments"></a>Açıklamalar  
 Bir veri kaynağı doğru bir şekilde dosya sistemi içeriğini temsil eder ve düzgün bir şekilde özel durumları işler oluşturmak için gerekli olan bazı karmaşıklığı yoktur. Bu bölümdeki örneklerde, bir anlık görüntü koleksiyonunu oluşturmak <xref:System.IO.FileInfo> belirtilen kök klasör altındaki tüm dosyaları ve tüm alt klasörlerindeki temsil eden nesneleri. Her gerçek durumuyla <xref:System.IO.FileInfo> ne zaman başlar ve son Sorguyu yürüten arasında zaman içinde değişebilir. Örneğin, bir listesini oluşturabilirsiniz <xref:System.IO.FileInfo> veri kaynağı olarak kullanılacak nesne. Erişmeye çalışırsanız `Length` özelliği bir sorgu <xref:System.IO.FileInfo> nesne değerini güncelleştirmek üzere dosya sisteminde erişmeye çalışır `Length`. Dosya artık mevcut değilse, erişmenizi sağlayacak bir <xref:System.IO.FileNotFoundException> sorgunuzda, olsa bile, yok sorguladığınız dosya sistemi doğrudan. Bu bölümde bazı sorgular, bu belirli özel durumları, bazı durumlarda tüketen ayrı bir yöntem kullanın. Başka bir seçeneği kullanarak dinamik olarak güncelleştirilen veri kaynağınız tutmaktır <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects'in (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
