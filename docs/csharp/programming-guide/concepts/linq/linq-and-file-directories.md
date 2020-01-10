---
title: LINQ ve dosya dizinleri (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: fe503584e7d14e8d1dd281eb644f0723782feb4a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714620"
---
# <a name="linq-and-file-directories-c"></a>LINQ ve dosya dizinleri (C#)

Birçok dosya sistemi işlemi aslında sorgular ve bu nedenle LINQ yaklaşımına uygundur.  
  
 Bu bölümdeki sorgular bozucu değildir. Özgün dosyaların veya klasörlerin içeriğini değiştirmek için kullanılmaz. Bu, sorguların hiçbir yan etkiye neden olmaması gerektiğine yönelik kuralı izler. Genel olarak, kaynak verileri değiştiren tüm kodlar (oluşturma/güncelleştirme/silme işleçleri de dahil olmak üzere) yalnızca verileri sorgulayan koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Belirtilen öznitelik veya ada sahip dosyaları sorgulama (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)\
 <xref:System.IO.FileInfo> nesnesinin bir veya daha fazla özelliğini inceleyerek dosyaların nasıl aranacağını gösterir.  
  
 [Dosyaları uzantıya göre gruplama (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)\
 <xref:System.IO.FileInfo> nesne gruplarının dosya adı uzantısına göre nasıl geri alınacağını gösterir.  
  
 [Bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)\
 Belirtilen bir dizin ağacındaki tüm dosyalardaki toplam bayt sayısının nasıl geri yükleneceğini gösterir.  
  
 [İki klasörün içeriğini karşılaştırma (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)s  
 Belirtilen iki klasörde bulunan tüm dosyaları ve aynı zamanda bir klasörde bulunan ancak diğeri olmayan tüm dosyaları döndürmeyi gösterir.  
  
 [Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)\
 Bir dizin ağacında en büyük veya en küçük dosyanın veya belirli bir sayıdaki dosyanın nasıl döndürülmeli olduğunu gösterir.  
  
 [Bir dizin ağacında (LINQ) yinelenen dosyaları sorgulama (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)\
 Belirtilen bir dizin ağacındaki birden fazla konumda gerçekleşen tüm dosya adlarının nasıl gruplandıralınacağını gösterir. Ayrıca, özel bir karşılaştırıcıyı temel alan daha karmaşık karşılaştırmalar yapmayı gösterir.  
  
 [Bir klasördeki dosyaların içeriğini sorgulama (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)\
 Bir ağaçtaki klasörlerin nasıl tekrarlanması, her dosyanın nasıl açılacağı ve dosyanın içeriğini sorgulama işlemlerinin nasıl yapılacağını gösterir.  
  
## <a name="comments"></a>Açıklamalar  
 Dosya sisteminin içeriğini doğru bir şekilde temsil eden bir veri kaynağı oluşturma konusunda bazı karmaşıklıklar vardır ve özel durumları düzgün bir şekilde işler. Bu bölümdeki örneklerde, belirtilen bir kök klasörü ve tüm alt klasörleri altındaki tüm dosyaları temsil eden <xref:System.IO.FileInfo> nesnelerinin bir anlık görüntü koleksiyonu oluşturulur. Her bir <xref:System.IO.FileInfo> gerçek durumu, bir sorgu yürütme ve sonlandırma arasındaki sürede değişebilir. Örneğin, bir veri kaynağı olarak kullanmak üzere <xref:System.IO.FileInfo> nesnelerinin bir listesini oluşturabilirsiniz. Bir sorgudaki `Length` özelliğine erişmeyi denerseniz, <xref:System.IO.FileInfo> nesnesi `Length`değerini güncelleştirmek için dosya sistemine erişmeye çalışır. Dosya artık yoksa, dosya sistemini doğrudan sorguladığınız halde sorgunuzda bir <xref:System.IO.FileNotFoundException> alırsınız. Bu bölümdeki bazı sorgular belirli durumlarda bu özel durumları tüketen ayrı bir yöntem kullanır. Diğer bir seçenek de <xref:System.IO.FileSystemWatcher>kullanarak veri kaynağınızı dinamik olarak güncel tutkullanmaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (C#)](./linq-to-objects.md)
