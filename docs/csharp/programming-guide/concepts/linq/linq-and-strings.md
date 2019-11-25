---
title: LINQ ve dizeler (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: fb1714c54331ead80cd28435cf3ed1c4c54a704e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140901"
---
# <a name="linq-and-strings-c"></a>LINQ ve dizeler (C#)

LINQ, dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir. Bu, özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir. LINQ sorguları, geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir. Örneğin, LINQ kullanarak sorgulayabilmeniz veya değiştiremeyeceğiniz bir dize dizisi oluşturmak için <xref:System.String.Split%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Bir LINQ sorgusunun `where` yan tümcesinde <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Aynı şekilde, bir normal ifade tarafından döndürülen <xref:System.Text.RegularExpressions.MatchCollection> sonuçlarını sorgulamak veya değiştirmek için LINQ kullanabilirsiniz.

Yarı yapılandırılmış metin verilerini XML 'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: CSV DOSYALARıNDAN XML oluşturma](how-to-generate-xml-from-csv-files.md).

Bu bölümdeki örnekler iki kategoriye ayrılır:

## <a name="querying-a-block-of-text"></a>Metin bloğunu sorgulama

<xref:System.String.Split%2A?displayProperty=nameWithType> yöntemini veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemini kullanarak bunları bir daha küçük dizeler dizisine bölerek metin bloklarını sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz. Kaynak metni sözcükler, cümleler, paragraflar, sayfalar veya diğer ölçütlere bölebilir ve ardından sorgunuzda gerekliyse ek bölmeler gerçekleştirebilirsiniz.

- [Dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Metin üzerinde basit sorgulama için LINQ 'ın nasıl kullanılacağını gösterir.

- [Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Metin dosyalarının rastgele sınırlarda nasıl bölüneceği ve her parçaya yönelik sorguların nasıl gerçekleştirileceğini gösterir.

- [Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Bir dizenin sorgulanabilir bir tür olduğunu gösterir.

- [LINQ sorgularını normal ifadelerle birleştirme (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Filtrelenmiş sorgu sonuçlarında karmaşık model eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.

## <a name="querying-semi-structured-data-in-text-format"></a>Yarı yapılandırılmış verileri metin biçiminde sorgulama

Birçok farklı metin dosyası türü, genellikle sekme veya virgülle ayrılmış dosyalar ya da sabit uzunluklu çizgiler gibi benzer biçimlendirmeler içeren bir dizi satırdan oluşur. Bu tür bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ kullanabilirsiniz. LINQ sorguları Ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.

- [Nasıl yapılır: Iki liste arasında küme farkını bulma (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Bir listede bulunan ancak diğeri olmayan tüm dizelerin nasıl bulunacağını gösterir.

- [Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ)C#()](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Metin çizgilerinin herhangi bir sözcük veya alana göre nasıl sıralanacağını gösterir.

- [Nasıl yapılır: ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Bir. csv dosyasındaki bir satırdaki alanların nasıl yeniden oluşturulduğunu gösterir.

- [Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Dize listelerinin çeşitli yollarla nasıl birleştirileceğini gösterir.

- [Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Birden çok metin dosyasını veri kaynağı olarak kullanarak nasıl nesne koleksiyonları oluşturulacağını gösterir.

- [Nasıl yapılır: farklı dosyalardan Içerik ekleme (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  İki listedeki dizelerin, eşleşen bir anahtar kullanılarak tek bir dize içinde nasıl birleştirileceğini gösterir.

- [Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (LINQ)C#()](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturulacağını gösterir.

- [CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  . Csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl gerçekleştirileceğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](index.md)
- [Nasıl yapılır: CSV Dosyalarından XML Oluşturma](how-to-generate-xml-from-csv-files.md)
