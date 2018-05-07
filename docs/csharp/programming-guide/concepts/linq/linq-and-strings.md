---
title: LINQ ve dizeler (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: a297aec0a33893c643be337c356e304cdcd375ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-and-strings-c"></a>LINQ ve dizeler (C#)
LINQ Sorgu ve dizeler ve koleksiyonları dizeleri dönüştürmek için kullanılabilir. Metin dosyaları yarı yapılandırılmış veriyle özellikle yararlı olabilir. LINQ sorgularını geleneksel dize işlevleri ve normal ifadeler ile birleştirilebilir. Örneğin, kullanabileceğiniz <xref:System.String.Split%2A> veya <xref:System.Text.RegularExpressions.Regex.Split%2A> sonra sorgu veya LINQ kullanarak değiştirmek için bir dizeler dizisi oluşturmak için yöntemi. Kullanabileceğiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yönteminde `where` bir LINQ sorgu yan tümcesi. LINQ Sorgu veya değiştirmek için kullanabileceğiniz <xref:System.Text.RegularExpressions.MatchCollection> normal bir ifade tarafından döndürülen sonuç.  
  
 Bu bölümde açıklanan teknikleri, yarı yapılandırılmış metin verilerini XML'e dönüştürmek için de kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: XML oluşturmak CSV dosyalarından](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd).  
  
 Bu bölümdeki örnekleri iki kategoriye ayrılır:  
  
## <a name="querying-a-block-of-text"></a>Bir metin bloğunu sorgulama  
 Sorgu, çözümlemek ve daha küçük dizeleri sorgulanabilir bir diziye bölerek kullanarak metin blokları değiştirme <xref:System.String.Split%2A> yöntemi veya <xref:System.Text.RegularExpressions.Regex.Split%2A> yöntemi. Kaynak metni sözcükler, cümle, paragraf, sayfalar veya başka bir ölçüt bölme ve sorgunuzda gerekirse ek bölmelerini gerçekleştirin.  
  
 [Nasıl yapılır: bir sözcüğün bir dizede (LINQ) (C#) yinelemeleri Say](../../../../csharp/programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Basit metin sorgulamaya LINQ kullanmayı gösterir.  
  
 [Nasıl yapılır: sözcükleri (LINQ) (C#) belirtilen bir kümesini içeren cümleleri sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)  
 Metin dosyaları rasgele sınırlarındaki ayırma ve her bölümü sorguları gerçekleştirmek nasıl gösterir.  
  
 [Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakter için](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-characters-in-a-string-linq.md)  
 Bir dize sorgulanabilir türü olduğunu gösterir.  
  
 [Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)  
 Normal ifadeler LINQ sorgularında karmaşık desen filtrelenmiş sorgu sonuçlarına eşleştirme için kullanmayı gösterir.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Metin biçimindeki yarı yapılandırılmış veri sorgulama  
 Sekme veya virgülle ayrılmış dosyalar veya sabit uzunluklu satırları gibi benzer biçimlendirmeye sahip genellikle satırları, bir dizi farklı türlerde metin dosyaları oluşur. Belleğe gibi bir metin dosyası okuma sonra LINQ Sorgu ve/veya satırları değiştirmek için kullanabilirsiniz. LINQ sorguları da birden fazla kaynaktan veri birleştirme görevini basitleştirir.  
  
 [Nasıl yapılır: (LINQ) (C#) iki liste arasında ayarlanmış farkı bulma](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)  
 Bir liste ancak diğer var olan tüm dizeleri bulmak gösterilmiştir.  
  
 [Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Metin satırlarını herhangi bir sözcük veya alana göre sıralamak gösterilmiştir.  
  
 [Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama](../../../../csharp/programming-guide/concepts/linq/how-to-reorder-the-fields-of-a-delimited-file-linq.md)  
 Bir .csv dosyası bir satırda alanları yeniden sıralamak gösterilmiştir.  
  
 [Nasıl yapılır: dize koleksiyonlarını (LINQ) (C#) birleştirme ve karşılaştırma](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 Dize listesi çeşitli şekillerde birleştirmek gösterilmiştir.  
  
 [Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Veri kaynakları olarak birden çok metin dosyalarını kullanarak nesne koleksiyonları oluşturulacağını gösterir.  
  
 [Nasıl yapılır: (LINQ) (C#) farklı dosyalardan içerik birleştirme](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 İki liste dizelerde eşleşen bir anahtarı'nı kullanarak tek bir dize halinde birleştirmek gösterilmiştir.  
  
 [Nasıl yapılır: bir dosya grupları (LINQ) (C#) kullanarak birden çok dosyaya bölme](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Bir veri kaynağı olarak tek bir dosya kullanarak yeni dosyalar oluşturulacağını gösterir.  
  
 [Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (C#) sütun değerlerini hesaplama](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 .Csv dosyaları metin veriler üzerinde matematiksel hesaplamalar gösterilmektedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [Nasıl yapılır: CSV Dosyalarından XML Oluşturma](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
