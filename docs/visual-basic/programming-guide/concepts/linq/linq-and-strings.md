---
title: LINQ ve Dizeler
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: ee2a44175e8546f879473a3af6bf1a2de92d2501
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549855"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ ve dizeler (Visual Basic)
LINQ, dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir. Bu, özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir. LINQ sorguları, geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir. Örneğin, <xref:System.String.Split%2A> <xref:System.Text.RegularExpressions.Regex.Split%2A> daha sonra LINQ kullanarak sorgulayabilmeniz veya değiştiremeyeceğiniz bir dize dizisi oluşturmak için veya yöntemini kullanabilirsiniz. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> `where` Bir LINQ sorgusunun yan tümcesindeki yöntemini kullanabilirsiniz. Aynı şekilde, <xref:System.Text.RegularExpressions.MatchCollection> bir normal ifade tarafından döndürülen sonuçları sorgulamak veya değiştirmek IÇIN LINQ kullanabilirsiniz.  
  
 Yarı yapılandırılmış metin verilerini XML 'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: CSV DOSYALARıNDAN XML oluşturma](../../../../standard/linq/generate-xml-csv-files.md).  
  
 Bu bölümdeki örnekler iki kategoriye ayrılır:  
  
## <a name="querying-a-block-of-text"></a>Metin bloğunu sorgulama  
 Yöntemini veya yöntemini kullanarak bunları bir daha küçük dizeler dizisine bölerek metin bloklarını sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz <xref:System.String.Split%2A> <xref:System.Text.RegularExpressions.Regex.Split%2A> . Kaynak metni sözcükler, cümleler, paragraflar, sayfalar veya diğer ölçütlere bölebilir ve ardından sorgunuzda gerekliyse ek bölmeler gerçekleştirebilirsiniz.  
  
 [Nasıl yapılır: dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Metin üzerinde basit sorgulama için LINQ 'ın nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Metin dosyalarının rastgele sınırlarda nasıl bölüneceği ve her parçaya yönelik sorguların nasıl gerçekleştirileceğini gösterir.  
  
 [Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Bir dizenin sorgulanabilir bir tür olduğunu gösterir.  
  
 [LINQ sorgularını normal ifadelerle birleştirme (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Filtrelenmiş sorgu sonuçlarında karmaşık model eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Yarı yapılandırılmış verileri metin biçiminde sorgulama  
 Birçok farklı metin dosyası türü, genellikle sekme veya virgülle ayrılmış dosyalar ya da sabit uzunluklu çizgiler gibi benzer biçimlendirmeler içeren bir dizi satırdan oluşur. Bu tür bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ kullanabilirsiniz. LINQ sorguları Ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.  
  
 [Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Bir listede bulunan ancak diğeri olmayan tüm dizelerin nasıl bulunacağını gösterir.  
  
 [Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Metin çizgilerinin herhangi bir sözcük veya alana göre nasıl sıralanacağını gösterir.  
  
 [Nasıl yapılır: ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Bir. csv dosyasındaki bir satırdaki alanların nasıl yeniden oluşturulduğunu gösterir.  
  
 [Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Dize listelerinin çeşitli yollarla nasıl birleştirileceğini gösterir.  
  
 [Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Birden çok metin dosyasını veri kaynağı olarak kullanarak nasıl nesne koleksiyonları oluşturulacağını gösterir.  
  
 [Nasıl yapılır: farklı dosyalardan Içerik ekleme (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 İki listedeki dizelerin, eşleşen bir anahtar kullanılarak tek bir dize içinde nasıl birleştirileceğini gösterir.  
  
 [Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturulacağını gösterir.  
  
 [Nasıl yapılır: CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 . Csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl gerçekleştirileceğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)
- [Nasıl yapılır: CSV dosyalarından XML oluşturma](../../../../standard/linq/generate-xml-csv-files.md)
