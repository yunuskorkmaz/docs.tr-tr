---
title: LINQ ve Dosya Dizinleri
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 670611cd285a1b1f2602e2c700c2bdeb56db943f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100171"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ ve dosya dizinleri (Visual Basic)

Birçok dosya sistemi işlemi aslında sorgular ve bu nedenle LINQ yaklaşımına uygundur.  
  
 Bu bölümdeki sorguların bozucu olmadığına unutmayın. Özgün dosyaların veya klasörlerin içeriğini değiştirmek için kullanılmaz. Bu, sorguların hiçbir yan etkiye neden olmaması gerektiğine yönelik kuralı izler. Genel olarak, kaynak verileri değiştiren tüm kodlar (oluşturma/güncelleştirme/silme işleçleri de dahil olmak üzere) yalnızca verileri sorgulayan koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)](how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Nesnesinin bir veya daha fazla özelliğini inceleyerek dosyaların nasıl aranacağını gösterir <xref:System.IO.FileInfo> .  
  
 [Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)](how-to-group-files-by-extension-linq.md)  
 <xref:System.IO.FileInfo>Nesne gruplarının dosya adı uzantısına göre nasıl geri alınacağını gösterir.  
  
 [Nasıl yapılır: bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (Visual Basic)](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Belirtilen bir dizin ağacındaki tüm dosyalardaki toplam bayt sayısının nasıl geri yükleneceğini gösterir.  
  
 [Nasıl yapılır: Iki klasörün Içeriğini karşılaştırma (LINQ) (Visual Basic)](how-to-compare-the-contents-of-two-folders-linq.md)s  
 Belirtilen iki klasörde bulunan tüm dosyaları ve aynı zamanda bir klasörde bulunan ancak diğeri olmayan tüm dosyaları döndürmeyi gösterir.  
  
 [Nasıl yapılır: bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (Visual Basic)](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Bir dizin ağacında en büyük veya en küçük dosyanın veya belirli bir sayıdaki dosyanın nasıl döndürülmeli olduğunu gösterir.  
  
 [Nasıl yapılır: bir dizin ağacında (LINQ) yinelenen dosyalar için sorgu (Visual Basic)](how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen bir dizin ağacındaki birden fazla konumda gerçekleşen tüm dosya adlarının nasıl gruplandıralınacağını gösterir. Ayrıca, özel bir karşılaştırıcıyı temel alan daha karmaşık karşılaştırmalar yapmayı gösterir.  
  
 [Bir klasördeki dosyaların içeriğini sorgulama (LINQ) (Visual Basic)](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Bir ağaçtaki klasörlerin nasıl tekrarlanması, her dosyanın nasıl açılacağı ve dosyanın içeriğini sorgulama işlemlerinin nasıl yapılacağını gösterir.  
  
## <a name="comments"></a>Yorumlar  

 Dosya sisteminin içeriğini doğru bir şekilde temsil eden bir veri kaynağı oluşturma konusunda bazı karmaşıklıklar vardır ve özel durumları düzgün bir şekilde işler. Bu bölümdeki örneklerde, <xref:System.IO.FileInfo> belirtilen bir kök klasörü ve tüm alt klasörleri altındaki tüm dosyaları temsil eden nesnelerin anlık görüntü koleksiyonu oluşturulur. Her birinin gerçek durumu <xref:System.IO.FileInfo> bir sorgu yürütme ve sonlandırma arasındaki sürede değişebilir. Örneğin, <xref:System.IO.FileInfo> bir veri kaynağı olarak kullanmak üzere bir nesne listesi oluşturabilirsiniz. `Length`Bir sorgudaki özelliğe erişmeyi denerseniz, <xref:System.IO.FileInfo> nesne değerini güncelleştirmek için dosya sistemine erişmeye çalışacaktır `Length` . Dosya artık yoksa, <xref:System.IO.FileNotFoundException> dosya sistemini doğrudan sorguladığınız halde, sorgunuzda bir a alacaksınız. Bu bölümdeki bazı sorgular belirli durumlarda bu özel durumları tüketen ayrı bir yöntem kullanır. Diğer bir seçenek, kullanarak veri kaynağınızı dinamik olarak güncel tutkullanmaktır <xref:System.IO.FileSystemWatcher> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
