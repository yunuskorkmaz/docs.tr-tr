---
title: LINQ ve dosya dizinleri (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: fe503584e7d14e8d1dd281eb644f0723782feb4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714620"
---
# <a name="linq-and-file-directories-c"></a>LINQ ve dosya dizinleri (C#)

Birçok dosya sistemi işlemleri aslında sorgulardır ve bu nedenle LINQ yaklaşımına çok uygundur.  
  
 Bu bölümdeki sorgular tahrip edici değildir. Bunlar orijinal dosya veya klasörlerin içeriğini değiştirmek için kullanılmaz. Bu, sorguların herhangi bir yan etkiye neden olmaması gerektiği kuralını izler. Genel olarak, kaynak verileri değiştiren tüm kodlar (oluşturma / güncelleştirme / silme işleçleri gerçekleştiren sorgular dahil) yalnızca verileri sorgulayan koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Belirli bir öznitelik veya ada sahip dosyalar için sorgulama (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)\
 <xref:System.IO.FileInfo> Nesnesinin bir veya daha fazla özelliğini inceleyerek dosyaların nasıl arandığını gösterir.  
  
 [Uzantıya göre dosya gruplandırma (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)\
 Dosya adı uzantısına <xref:System.IO.FileInfo> göre nesne gruplarının nasıl döndürüleceklerini gösterir.  
  
 [Klasörler kümesindeki toplam bayt sayısı (LINQ) (C#) için sorgulama](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)\
 Belirtilen bir dizin ağacındaki tüm dosyalardaki toplam bayt sayısını nasıl döndüreceklerini gösterir.  
  
 [Nasıl iki klasör (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)s içeriğini karşılaştırmak için  
 Belirtilen iki klasörde bulunan tüm dosyaların ve ayrıca bir klasörde bulunan ancak diğerinde bulunmayan tüm dosyaların nasıl döndürüleceklerini gösterir.  
  
 [Dizin ağacındaki (LINQ) (C#) en büyük dosya veya dosyaları sorgulama](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)\
 Dizin ağacındaki en büyük veya en küçük dosyanın veya belirli sayıda dosyanın nasıl döndürüleceklerini gösterir.  
  
 [Dizin ağacında yinelenen dosyalar için sorgulama (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)\
 Belirli bir dizin ağacında birden fazla konumda oluşan tüm dosya adları için nasıl gruplanın yapılacağını gösterir. Ayrıca, özel bir karşılayıcıya dayalı daha karmaşık karşılaştırmaların nasıl gerçekleştirildirilebildiğini de gösterir.  
  
 [Klasördeki dosyaların içeriği nasıl sorgulanır (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)\
 Bir ağaçtaki klasörler arasında nasıl ayin yapılacağını, her dosyayı nasıl açacağını ve dosyanın içeriğini nasıl sorgulayılacağını gösterir.  
  
## <a name="comments"></a>Yorumlar  
 Dosya sisteminin içeriğini doğru bir şekilde temsil eden ve özel durumları incelikle işleyen bir veri kaynağı oluşturmada bazı karmaşıklıklar söz konusudur. Bu bölümdeki örnekler, belirtilen <xref:System.IO.FileInfo> kök klasörün altındaki tüm dosyaları ve tüm alt klasörlerini temsil eden nesnelerin anlık görüntüsü koleksiyonunu oluşturur. Her <xref:System.IO.FileInfo> birinin gerçek durumu, bir sorguyu yürütmeye başladığınız ve son gördüğünüz zaman arasındaki süre içinde değişebilir. Örneğin, veri kaynağı olarak <xref:System.IO.FileInfo> kullanılacak nesnelerin bir listesini oluşturabilirsiniz. Bir sorgudaki `Length` özelliğe erişmeye çalışırsanız, <xref:System.IO.FileInfo> nesne değerini güncelleştirmek için dosya `Length`sistemine erişmeye çalışır. Dosya artık yoksa, doğrudan dosya <xref:System.IO.FileNotFoundException> sistemini sorgulamasanız bile, sorgunuzda bir soru alırsınız. Bu bölümdeki bazı sorgular, bazı durumlarda bu özel özel durumları kullanan ayrı bir yöntem kullanır. Başka bir seçenek kullanarak veri kaynağınızı dinamik <xref:System.IO.FileSystemWatcher>olarak güncel tutmaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (C#)](./linq-to-objects.md)
