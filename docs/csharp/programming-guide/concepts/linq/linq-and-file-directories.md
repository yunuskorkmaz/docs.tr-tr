---
title: LINQ ve dosya dizinleri (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: 1d2109fe7f4f907317275188057fa6e5e71b2679
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591979"
---
# <a name="linq-and-file-directories-c"></a>LINQ ve dosya dizinleri (C#)
Birçok dosya sistemi işlemi aslında sorgular ve bu nedenle LINQ yaklaşımına uygundur.  
  
 Bu bölümdeki sorguların bozucu olmadığına unutmayın. Özgün dosyaların veya klasörlerin içeriğini değiştirmek için kullanılmaz. Bu, sorguların hiçbir yan etkiye neden olmaması gerektiğine yönelik kuralı izler. Genel olarak, kaynak verileri değiştiren tüm kodlar (oluşturma/güncelleştirme/silme işleçleri de dahil olmak üzere) yalnızca verileri sorgulayan koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: Belirtilen bir özniteliğe veya ada (C#) sahip dosyaları sorgula](./how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <xref:System.IO.FileInfo> Nesnesinin bir veya daha fazla özelliğini inceleyerek dosyaların nasıl aranacağını gösterir.  
  
 [Nasıl yapılır: Dosyaları uzantıya göre Gruplandır (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)  
 <xref:System.IO.FileInfo> Nesne gruplarının dosya adı uzantısına göre nasıl geri alınacağını gösterir.  
  
 [Nasıl yapılır: Bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Belirtilen bir dizin ağacındaki tüm dosyalardaki toplam bayt sayısının nasıl geri yükleneceğini gösterir.  
  
 [Nasıl yapılır: İki klasörün içeriğini karşılaştırma (LINQ) (C#) s](./how-to-compare-the-contents-of-two-folders-linq.md)  
 Belirtilen iki klasörde bulunan tüm dosyaları ve aynı zamanda bir klasörde bulunan ancak diğeri olmayan tüm dosyaları döndürmeyi gösterir.  
  
 [Nasıl yapılır: Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Bir dizin ağacında en büyük veya en küçük dosyanın veya belirli bir sayıdaki dosyanın nasıl döndürülmeli olduğunu gösterir.  
  
 [Nasıl yapılır: Bir dizin ağacında (LINQ) (C#) yinelenen dosyalar için sorgu](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen bir dizin ağacındaki birden fazla konumda gerçekleşen tüm dosya adlarının nasıl gruplandıralınacağını gösterir. Ayrıca, özel bir karşılaştırıcıyı temel alan daha karmaşık karşılaştırmalar yapmayı gösterir.  
  
 [Nasıl yapılır: Bir klasördeki dosyaların Içeriğini sorgulama (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Bir ağaçtaki klasörlerin nasıl tekrarlanması, her dosyanın nasıl açılacağı ve dosyanın içeriğini sorgulama işlemlerinin nasıl yapılacağını gösterir.  
  
## <a name="comments"></a>Açıklamalar  
 Dosya sisteminin içeriğini doğru bir şekilde temsil eden bir veri kaynağı oluşturma konusunda bazı karmaşıklıklar vardır ve özel durumları düzgün bir şekilde işler. Bu bölümdeki örneklerde, belirtilen bir kök klasörü ve tüm <xref:System.IO.FileInfo> alt klasörleri altındaki tüm dosyaları temsil eden nesnelerin anlık görüntü koleksiyonu oluşturulur. Her <xref:System.IO.FileInfo> birinin gerçek durumu bir sorgu yürütme ve sonlandırma arasındaki sürede değişebilir. Örneğin, bir veri kaynağı olarak kullanmak üzere bir <xref:System.IO.FileInfo> nesne listesi oluşturabilirsiniz. Bir sorgudaki `Length` özelliğe erişmeyi denerseniz <xref:System.IO.FileInfo> , nesne değerini güncelleştirmek `Length`için dosya sistemine erişmeye çalışacaktır. Dosya artık yoksa, dosya sistemini doğrudan sorguladığınız halde, <xref:System.IO.FileNotFoundException> sorgunuzda bir a alacaksınız. Bu bölümdeki bazı sorgular belirli durumlarda bu özel durumları tüketen ayrı bir yöntem kullanır. Diğer bir seçenek, <xref:System.IO.FileSystemWatcher>kullanarak veri kaynağınızı dinamik olarak güncel tutkullanmaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (C#)](./linq-to-objects.md)
