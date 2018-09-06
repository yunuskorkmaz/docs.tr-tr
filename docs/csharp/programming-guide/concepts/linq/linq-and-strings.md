---
title: LINQ ve dizeler (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: da7a35f0fd66d1f7b8a72550c175b5428242fbc1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886506"
---
# <a name="linq-and-strings-c"></a>LINQ ve dizeler (C#)

LINQ Sorgu dizeleri ve dizelerden oluşan koleksiyonları dönüştürmek için kullanılabilir. Metin dosyalarında yarı yapısal verilerle özellikle yararlı olabilir. LINQ sorguları, geleneksel dize işlevleri ve normal ifadeler ile birleştirilebilir. Örneğin, kullanabileceğiniz <xref:System.String.Split%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> sonra sorgulayabilir veya LINQ kullanarak değiştirme dizeleri bir dizi oluşturmak için yöntemi. Kullanabileceğiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yönteminde `where` bir LINQ sorgu yan tümcesi. LINQ Sorgu veya değiştirmek için kullanabileceğiniz <xref:System.Text.RegularExpressions.MatchCollection> normal bir ifade tarafından döndürülen sonuç.

Bu bölümde açıklanan olan tekniklerle da XML'e yarı yapılandırılmış metin verileri dönüştürmek için de kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: CSV dosyalarından XML oluşturma](how-to-generate-xml-from-csv-files.md).

Bu bölümdeki örnekler, iki kategoriye ayrılır:

## <a name="querying-a-block-of-text"></a>Metin bloğu sorgulama

Sorgu, analiz ve daha küçük dizeleri sorgulanabilir bir diziye bölerek kullanarak metin blokları değiştirme <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemi. Kaynak metni sözcükler, cümle, paragraf, sayfaları veya başka bir ölçüt bölmek ve sorgunuzda gerekirse ek bölmelerini gerçekleştirin.

- [Nasıl yapılır: bir sözcüğün bir dizede (LINQ) (C#) sayma](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Basit metin üzerinde sorgulamak için LINQ kullanma işlemi gösterilmektedir.

- [Nasıl yapılır: belirli bir sözcükler (LINQ) (C#) kümesini içeren cümleleri sorgulama](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Metin dosyaları rastgele sınırlarındaki bölme ve her parça karşı sorguları gerçekleştirmeyi gösterir.

- [Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakterleri](how-to-query-for-characters-in-a-string-linq.md)

  Bir dize sorgulanabilir tür olduğunu gösterir.

- [Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme](how-to-combine-linq-queries-with-regular-expressions.md)

  Filtrelenmiş sorgu sonuçlarına karmaşık desen için LINQ sorgularında normal ifadeleri kullanma işlemi gösterilmektedir.

## <a name="querying-semi-structured-data-in-text-format"></a>Metin biçimindeki yarı yapılandırılmış verileri Sorgulama

Satırları, genellikle sekme veya virgülle sınırlandırılmış dosyalar veya sabit uzunluklu satırları gibi benzer biçimlendirmeye sahip olan bir dizi farklı türlerde metin dosyaları oluşur. Bu tür bir metin dosyası belleğe okuduktan sonra sorgu ve/veya satırları değiştirmek için LINQ kullanabilirsiniz. LINQ sorguları ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.

- [Nasıl yapılır: (LINQ) (C#) iki liste arasında ayarlanmış farkı bulma](how-to-find-the-set-difference-between-two-lists-linq.md)

  Bir liste ancak diğer mevcut olan tüm dizeleri bulmak gösterilmektedir.

- [Nasıl yapılır: herhangi bir sözcük veya alana (LINQ) (C#) göre filtre metin verilerini sıralama veya](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Herhangi bir sözcük veya alana göre metin satırlarını sıralama işlemi gösterilmektedir.

- [Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Bir .csv dosyası bir satırda alanları yeniden sıralama işlemi gösterilmektedir.

- [Nasıl yapılır: dize koleksiyonlarını (LINQ) (C#) birleştirme ve karşılaştırma](how-to-combine-and-compare-string-collections-linq.md)

  Dize listesi çeşitli şekillerde birleştirme işlemi gösterilmektedir.

- [Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Veri kaynağı olarak birden çok metin dosyasını kullanarak nesne koleksiyonları oluşturma işlemi gösterilmektedir.

- [Nasıl yapılır: birleştirme dosyalardan içerik (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Eşleşen bir anahtar kullanarak iki liste dizelerde tek bir dize olarak birleştirilecek gösterilmektedir.

- [Nasıl yapılır: gruplar (LINQ) (C#) kullanarak bir dosyayı birden çok dosyaya bölme](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Veri kaynağı olarak tek bir dosyayı kullanarak yeni dosyalar oluşturma işlemi gösterilmektedir.

- [Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (C#) sütun değerlerini hesaplama](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Metin verileri .csv dosyalarındaki matematiksel hesaplamalar gerçekleştirmek nasıl gösterir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](index.md)
- [Nasıl yapılır: CSV Dosyalarından XML Oluşturma](how-to-generate-xml-from-csv-files.md)
