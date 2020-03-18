---
title: LINQ ve dizeleri (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: b805bc7318b8c5fe70ab1c060d1058a6bbc4f177
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635541"
---
# <a name="linq-and-strings-c"></a>LINQ ve dizeleri (C#)

LINQ, dizeleri ve dizeleri koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir. Özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir. LINQ sorguları geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir. Örneğin, LINQ kullanarak <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> sorgulayabildiğiniz veya değiştirebileceğiniz bir dizi dize oluşturmak için veya yöntemi kullanabilirsiniz. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Yöntemi LINQ sorgusunun `where` yan tümcesinde kullanabilirsiniz. Ayrıca, düzenli bir ifadeyle döndürülen <xref:System.Text.RegularExpressions.MatchCollection> sonuçları sorgulamak veya değiştirmek için LINQ'yi kullanabilirsiniz.

Yarı yapılandırılmış metin verilerini XML'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz. Daha fazla bilgi için [CSV dosyalarından XML nasıl oluşturacağıkonusunda](how-to-generate-xml-from-csv-files.md)bilgi alabiliyorum.

Bu bölümdeki örnekler iki kategoriye ayrılır:

## <a name="querying-a-block-of-text"></a>Metin bloğunu sorgulama

<xref:System.String.Split%2A?displayProperty=nameWithType> Yöntem veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemi kullanarak metin bloklarını sorgulanabilir küçük dizeleri diziye bölerek sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz. Kaynak metni sözcüklere, cümlelere, paragraflara, sayfalara veya diğer ölçütlere bölebilir ve sorgunuzda gerekirse ek bölmeler gerçekleştirebilirsiniz.

- [Bir dizedeki bir sözcüğün oluşumları nasıl sayilir (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Metin üzerinden basit sorgulama için LINQ'nin nasıl kullanılacağını gösterir.

- [Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Metin dosyalarını rasgele sınırlarda nasıl bölerve her bölüme karşı sorguların nasıl gerçekleştirilişini gösterir.

- [Dizedeki karakterler (LINQ) (C#) karakterleri sorgulama](how-to-query-for-characters-in-a-string-linq.md)

  Bir dize sorgulanabilir bir tür olduğunu gösterir.

- [LINQ sorgularını normal ifadelerle birleştirme (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Filtre uygulanmış sorgu sonuçlarında karmaşık desen eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.

## <a name="querying-semi-structured-data-in-text-format"></a>Yarı yapılandırılmış verileri metin biçiminde sorgulama

Birçok farklı metin dosyası türü, genellikle sekme veya virgülle sınırlandırılmış dosyalar veya sabit uzunluktaki satırlar gibi benzer biçimlendirmeye sahip bir dizi satırdan oluşur. Böyle bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ'yu kullanabilirsiniz. LINQ sorguları, birden çok kaynaktan gelen verileri birleştirme görevini de basitleştirir.

- [İki liste (LINQ) (C#) arasındaki küme farkı nasıl bulabilirim?](how-to-find-the-set-difference-between-two-lists-linq.md)

  Bir listede bulunan ancak diğerinde bulunmayan tüm dizeleri nasıl bulacağımı gösterir.

- [Metin verilerini herhangi bir sözcüğe veya alana göre sıralama veya filtreleme (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Metin çizgilerini herhangi bir sözcük veya alana göre nasıl sıralanır gösterir.

- [Sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  .csv dosyasındaki bir satırdaki alanların nasıl yeniden sıralanın gerektiğini gösterir.

- [Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Dize listelerini çeşitli şekillerde nasıl birleştirin.

- [Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Veri kaynağı olarak birden çok metin dosyasını kullanarak nesne koleksiyonlarının nasıl oluşturulurulur gösterir.

- [Farklı dosyalardan (LINQ) (C#) içerik birleştirme](how-to-join-content-from-dissimilar-files-linq.md)
  
  Eşleşen bir tuşu kullanarak iki listedeki dizeleri tek bir dize halinde nasıl birleştirin.

- [Grupları kullanarak bir dosyayı birçok dosyaya bölme (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturularak oluşturulabildiğini gösterir.

- [CSV metin dosyasındaki sütun değerlerini nasıl hesaplar (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  .csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl yapılacağını gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil-Tümleşik Sorgu (LINQ) (C#)](index.md)
- [CSV dosyalarından XML oluşturma](how-to-generate-xml-from-csv-files.md)
