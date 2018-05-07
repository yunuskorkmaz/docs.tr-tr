---
title: LINQ ve dizeler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: a76465b33a30d149cd6313e2628ee742e248ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-and-strings-visual-basic"></a>LINQ ve dizeler (Visual Basic)
LINQ Sorgu ve dizeler ve koleksiyonları dizeleri dönüştürmek için kullanılabilir. Metin dosyaları yarı yapılandırılmış veriyle özellikle yararlı olabilir. LINQ sorgularını geleneksel dize işlevleri ve normal ifadeler ile birleştirilebilir. Örneğin, kullanabileceğiniz <xref:System.String.Split%2A> veya <xref:System.Text.RegularExpressions.Regex.Split%2A> sonra sorgu veya LINQ kullanarak değiştirmek için bir dizeler dizisi oluşturmak için yöntemi. Kullanabileceğiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yönteminde `where` bir LINQ sorgu yan tümcesi. LINQ Sorgu veya değiştirmek için kullanabileceğiniz <xref:System.Text.RegularExpressions.MatchCollection> normal bir ifade tarafından döndürülen sonuç.  
  
 Bu bölümde açıklanan teknikleri, yarı yapılandırılmış metin verilerini XML'e dönüştürmek için de kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: XML oluşturmak CSV dosyalarından](how-to-generate-xml-from-csv-files.md).  
  
 Bu bölümdeki örnekleri iki kategoriye ayrılır:  
  
## <a name="querying-a-block-of-text"></a>Bir metin bloğunu sorgulama  
 Sorgu, çözümlemek ve daha küçük dizeleri sorgulanabilir bir diziye bölerek kullanarak metin blokları değiştirme <xref:System.String.Split%2A> yöntemi veya <xref:System.Text.RegularExpressions.Regex.Split%2A> yöntemi. Kaynak metni sözcükler, cümle, paragraf, sayfalar veya başka bir ölçüt bölme ve sorgunuzda gerekirse ek bölmelerini gerçekleştirin.  
  
 [Nasıl yapılır: bir sözcüğün bir dizede (LINQ) (Visual Basic) yinelemeleri Say](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Basit metin sorgulamaya LINQ kullanmayı gösterir.  
  
 [Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Metin dosyaları rasgele sınırlarındaki ayırma ve her bölümü sorguları gerçekleştirmek nasıl gösterir.  
  
 [Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizedeki karakter için](how-to-query-for-characters-in-a-string-linq.md)  
 Bir dize sorgulanabilir türü olduğunu gösterir.  
  
 [Nasıl yapılır: (Visual Basic) Normal ifadelerle LINQ sorgularını birleştirme](how-to-combine-linq-queries-with-regular-expressions.md)  
 Normal ifadeler LINQ sorgularında karmaşık desen filtrelenmiş sorgu sonuçlarına eşleştirme için kullanmayı gösterir.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Metin biçimindeki yarı yapılandırılmış veri sorgulama  
 Sekme veya virgülle ayrılmış dosyalar veya sabit uzunluklu satırları gibi benzer biçimlendirmeye sahip genellikle satırları, bir dizi farklı türlerde metin dosyaları oluşur. Belleğe gibi bir metin dosyası okuma sonra LINQ Sorgu ve/veya satırları değiştirmek için kullanabilirsiniz. LINQ sorguları da birden fazla kaynaktan veri birleştirme görevini basitleştirir.  
  
 [Nasıl yapılır: iki liste (LINQ) (Visual Basic) arasında ayarlanmış farkı bulma](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Bir liste ancak diğer var olan tüm dizeleri bulmak gösterilmiştir.  
  
 [Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Metin satırlarını herhangi bir sözcük veya alana göre sıralamak gösterilmiştir.  
  
 [Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (Visual Basic) alanlarını yeniden sıralama](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Bir .csv dosyası bir satırda alanları yeniden sıralamak gösterilmiştir.  
  
 [Nasıl yapılır: dize koleksiyonlarını (LINQ) (Visual Basic) birleştirme ve karşılaştırma](how-to-combine-and-compare-string-collections-linq.md)  
 Dize listesi çeşitli şekillerde birleştirmek gösterilmiştir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Veri kaynakları olarak birden çok metin dosyalarını kullanarak nesne koleksiyonları oluşturulacağını gösterir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) farklı dosyalardan içerik birleştirme](how-to-join-content-from-dissimilar-files-linq.md)  
 İki liste dizelerde eşleşen bir anahtarı'nı kullanarak tek bir dize halinde birleştirmek gösterilmiştir.  
  
 [Nasıl yapılır: bir dosya grupları (LINQ) (Visual Basic) kullanarak birden çok dosyaya bölme](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Bir veri kaynağı olarak tek bir dosya kullanarak yeni dosyalar oluşturulacağını gösterir.  
  
 [Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (Visual Basic) sütun değerlerini hesaplama](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 .Csv dosyaları metin veriler üzerinde matematiksel hesaplamalar gösterilmektedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)  
 [Nasıl yapılır: CSV Dosyalarından XML Oluşturma](how-to-generate-xml-from-csv-files.md)
