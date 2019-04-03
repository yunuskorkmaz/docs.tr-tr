---
title: LINQ ve dizeler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 7e0ebe64494182191dafa033ecbc38bad17180be
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818962"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ ve dizeler (Visual Basic)
LINQ Sorgu dizeleri ve dizelerden oluşan koleksiyonları dönüştürmek için kullanılabilir. Metin dosyalarında yarı yapısal verilerle özellikle yararlı olabilir. LINQ sorguları, geleneksel dize işlevleri ve normal ifadeler ile birleştirilebilir. Örneğin, kullanabileceğiniz <xref:System.String.Split%2A> veya <xref:System.Text.RegularExpressions.Regex.Split%2A> sonra sorgulayabilir veya LINQ kullanarak değiştirme dizeleri bir dizi oluşturmak için yöntemi. Kullanabileceğiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yönteminde `where` bir LINQ sorgu yan tümcesi. LINQ Sorgu veya değiştirmek için kullanabileceğiniz <xref:System.Text.RegularExpressions.MatchCollection> normal bir ifade tarafından döndürülen sonuç.  
  
 Bu bölümde açıklanan olan tekniklerle da XML'e yarı yapılandırılmış metin verileri dönüştürmek için de kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: CSV dosyalarından XML oluşturma](how-to-generate-xml-from-csv-files.md).  
  
 Bu bölümdeki örnekler, iki kategoriye ayrılır:  
  
## <a name="querying-a-block-of-text"></a>Metin bloğu sorgulama  
 Sorgu, analiz ve daha küçük dizeleri sorgulanabilir bir diziye bölerek kullanarak metin blokları değiştirme <xref:System.String.Split%2A> yöntemi veya <xref:System.Text.RegularExpressions.Regex.Split%2A> yöntemi. Kaynak metni sözcükler, cümle, paragraf, sayfaları veya başka bir ölçüt bölmek ve sorgunuzda gerekirse ek bölmelerini gerçekleştirin.  
  
 [Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) (Visual Basic) oluşum sayısı](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Basit metin üzerinde sorgulamak için LINQ kullanma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: Belirli bir sözcükler (LINQ) (Visual Basic) kümesini içeren cümleleri sorgulama](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Metin dosyaları rastgele sınırlarındaki bölme ve her parça karşı sorguları gerçekleştirmeyi gösterir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) bir dizedeki karakterleri sorgulama](how-to-query-for-characters-in-a-string-linq.md)  
 Bir dize sorgulanabilir tür olduğunu gösterir.  
  
 [Nasıl yapılır: (Visual Basic) Normal ifadelerle LINQ sorgularını birleştirme](how-to-combine-linq-queries-with-regular-expressions.md)  
 Filtrelenmiş sorgu sonuçlarına karmaşık desen için LINQ sorgularında normal ifadeleri kullanma işlemi gösterilmektedir.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Metin biçimindeki yarı yapılandırılmış verileri Sorgulama  
 Satırları, genellikle sekme veya virgülle sınırlandırılmış dosyalar veya sabit uzunluklu satırları gibi benzer biçimlendirmeye sahip olan bir dizi farklı türlerde metin dosyaları oluşur. Bu tür bir metin dosyası belleğe okuduktan sonra sorgu ve/veya satırları değiştirmek için LINQ kullanabilirsiniz. LINQ sorguları ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) iki liste arasında ayarlanmış farkı bulma](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Bir liste ancak diğer mevcut olan tüm dizeleri bulmak gösterilmektedir.  
  
 [Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) (Visual Basic) göre filtre metin verilerini sıralama veya](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Herhangi bir sözcük veya alana göre metin satırlarını sıralama işlemi gösterilmektedir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) sınırlandırılmış bir dosyanın alanlarını yeniden sıralama](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Bir .csv dosyası bir satırda alanları yeniden sıralama işlemi gösterilmektedir.  
  
 [Nasıl yapılır: Birleştirme ve karşılaştırma (LINQ) (Visual Basic) dize koleksiyonları](how-to-combine-and-compare-string-collections-linq.md)  
 Dize listesi çeşitli şekillerde birleştirme işlemi gösterilmektedir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Veri kaynağı olarak birden çok metin dosyasını kullanarak nesne koleksiyonları oluşturma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: Dosyalardan içerik (LINQ) (Visual Basic) katılın](how-to-join-content-from-dissimilar-files-linq.md)  
 Eşleşen bir anahtar kullanarak iki liste dizelerde tek bir dize olarak birleştirilecek gösterilmektedir.  
  
 [Nasıl yapılır: Gruplar (LINQ) (Visual Basic) kullanarak bir dosyayı birden çok dosyaya bölme](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Veri kaynağı olarak tek bir dosyayı kullanarak yeni dosyalar oluşturma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: İşlem sütun değerleri bir CSV metinde dosyasında (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Metin verileri .csv dosyalarındaki matematiksel hesaplamalar gerçekleştirmek nasıl gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)
- [Nasıl yapılır: CSV dosyalarından XML oluşturma](how-to-generate-xml-from-csv-files.md)
