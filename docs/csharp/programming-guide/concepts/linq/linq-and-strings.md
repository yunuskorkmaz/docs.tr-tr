---
title: LINQ ve dizeler (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c7a1b86cc611d5f38ceab814b4594f5ad953fbc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744628"
---
# <a name="linq-and-strings-c"></a>LINQ ve dizeler (C#)

LINQ Sorgu dizeleri ve dizelerden oluşan koleksiyonları dönüştürmek için kullanılabilir. Metin dosyalarında yarı yapısal verilerle özellikle yararlı olabilir. LINQ sorguları, geleneksel dize işlevleri ve normal ifadeler ile birleştirilebilir. Örneğin, kullanabileceğiniz <xref:System.String.Split%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> sonra sorgulayabilir veya LINQ kullanarak değiştirme dizeleri bir dizi oluşturmak için yöntemi. Kullanabileceğiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yönteminde `where` bir LINQ sorgu yan tümcesi. LINQ Sorgu veya değiştirmek için kullanabileceğiniz <xref:System.Text.RegularExpressions.MatchCollection> normal bir ifade tarafından döndürülen sonuç.

Bu bölümde açıklanan olan tekniklerle da XML'e yarı yapılandırılmış metin verileri dönüştürmek için de kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: CSV dosyalarından XML oluşturma](how-to-generate-xml-from-csv-files.md).

Bu bölümdeki örnekler, iki kategoriye ayrılır:

## <a name="querying-a-block-of-text"></a>Metin bloğu sorgulama

Sorgu, analiz ve daha küçük dizeleri sorgulanabilir bir diziye bölerek kullanarak metin blokları değiştirme <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemi. Kaynak metni sözcükler, cümle, paragraf, sayfaları veya başka bir ölçüt bölmek ve sorgunuzda gerekirse ek bölmelerini gerçekleştirin.

- [Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) geçtiğini sayma (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Basit metin üzerinde sorgulamak için LINQ kullanma işlemi gösterilmektedir.

- [Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Metin dosyaları rastgele sınırlarındaki bölme ve her parça karşı sorguları gerçekleştirmeyi gösterir.

- [Nasıl yapılır: (LINQ) bir dizedeki karakterleri sorgulama (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Bir dize sorgulanabilir tür olduğunu gösterir.

- [Nasıl yapılır: Normal ifadelerle LINQ sorgularını birleştirme (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Filtrelenmiş sorgu sonuçlarına karmaşık desen için LINQ sorgularında normal ifadeleri kullanma işlemi gösterilmektedir.

## <a name="querying-semi-structured-data-in-text-format"></a>Metin biçimindeki yarı yapılandırılmış verileri Sorgulama

Satırları, genellikle sekme veya virgülle sınırlandırılmış dosyalar veya sabit uzunluklu satırları gibi benzer biçimlendirmeye sahip olan bir dizi farklı türlerde metin dosyaları oluşur. Bu tür bir metin dosyası belleğe okuduktan sonra sorgu ve/veya satırları değiştirmek için LINQ kullanabilirsiniz. LINQ sorguları ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.

- [Nasıl yapılır: (LINQ) iki liste arasında ayarlanmış farkı bulma (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Bir liste ancak diğer mevcut olan tüm dizeleri bulmak gösterilmektedir.

- [Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) göre filtre metin verilerini sıralama veya (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Herhangi bir sözcük veya alana göre metin satırlarını sıralama işlemi gösterilmektedir.

- [Nasıl yapılır: (LINQ) sınırlandırılmış bir dosyanın alanlarını yeniden sıralama (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Bir .csv dosyası bir satırda alanları yeniden sıralama işlemi gösterilmektedir.

- [Nasıl yapılır: (LINQ) dize koleksiyonlarını birleştirme ve karşılaştırma (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Dize listesi çeşitli şekillerde birleştirme işlemi gösterilmektedir.

- [Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Veri kaynağı olarak birden çok metin dosyasını kullanarak nesne koleksiyonları oluşturma işlemi gösterilmektedir.

- [Nasıl yapılır: Dosyalardan içerik (LINQ) katılın (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Eşleşen bir anahtar kullanarak iki liste dizelerde tek bir dize olarak birleştirilecek gösterilmektedir.

- [Nasıl yapılır: Gruplar (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Veri kaynağı olarak tek bir dosyayı kullanarak yeni dosyalar oluşturma işlemi gösterilmektedir.

- [Nasıl yapılır: Sütun değerleri bir CSV metinde dosyasında (LINQ) işlem (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Metin verileri .csv dosyalarındaki matematiksel hesaplamalar gerçekleştirmek nasıl gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](index.md)
- [Nasıl yapılır: CSV dosyalarından XML oluşturma](how-to-generate-xml-from-csv-files.md)
