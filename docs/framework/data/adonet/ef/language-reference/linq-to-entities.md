---
title: LINQ - Varlıklar
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: 8a69d74966b99d78b4a7addaa4323d61d82ce8d5
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539766"
---
# <a name="linq-to-entities"></a>LINQ - Varlıklar
LINQ to Entities, geliştiricilerin Visual Basic veya Visual C# kullanarak varlık çerçevesi kavramsal modeline karşı sorgular yazmaya olanak tanıyan dil ile tümleşik sorgu (LINQ) destekler. Entity Framework sorguları nesne bağlamı karşı yürütülen komut ağaç sorguları tarafından temsil edilir. LINQ to Entities ağaç sorgular, Entity Framework sorguları yürütür ve Entity Framework ve LINQ tarafından kullanılan nesneleri döndürür komut dil ile tümleşik sorgu (LINQ) sorguları dönüştürür. Oluşturma ve bir LINQ to Entities sorgusunda yürütme işlemi aşağıda verilmiştir:  
  
1. Oluşturmak bir <xref:System.Data.Objects.ObjectQuery%601> gelen örnek <xref:System.Data.Objects.ObjectContext>.  
  
2. Bir LINQ to Entities sorgusunda C# veya Visual Basic kullanarak compose <xref:System.Data.Objects.ObjectQuery%601> örneği.  
  
3. LINQ standart sorgu işleçler ve ifadeler komut ağaçlarını dönüştürmek.  
  
4. Veri kaynağına karşı komut ağacı gösteriminde sorguyu yürütün. Veri kaynağı üzerinde yürütme sırasında oluşturulan özel durumlar, doğrudan istemciye kadar geçirilir.  
  
5. Sorgu sonuçları istemciye geri dönün.  
  
## <a name="constructing-an-objectquery-instance"></a>Bir ObjectQuery örneğinin oluşturma  
 <xref:System.Data.Objects.ObjectQuery%601> Genel sınıf bir sıfır veya daha fazla yazılı varlık koleksiyonunu döndüren bir sorgu temsil eder. Bir nesne sorgusu bağlamından el ile yapılandırılan yerine var olan nesne, genellikle oluşturulur ve her zaman bu nesne bağlamına ait. Bu bağlamı bağlantısı ve oluşturmak ve sorguyu yürütmek için gereken meta veri bilgileri sağlar. <xref:System.Data.Objects.ObjectQuery%601> Genel bir sınıf uygulayan <xref:System.Linq.IQueryable%601> genel arabirim, oluşturucu yöntemleri LINQ sorguları artımlı olarak oluşturulacak etkinleştirin. Ayrıca C# kullanarak varlık türü derleyicinin sağlayabilirsiniz `var` anahtar sözcüğü (`Dim` Visual Basic'te, yerel tür çıkarımı etkin).  
  
## <a name="composing-the-queries"></a>Sorguları oluşturma  
 Örneklerini <xref:System.Data.Objects.ObjectQuery%601> genel uygulayan genel sınıf <xref:System.Linq.IQueryable%601> arabirimi, veri kaynağı olarak Entities sorgularında LINQ için hizmet. Bir sorgu, veri kaynağından almak istediğiniz bilgi tam olarak belirtin. Bir sorgu, ayrıca nasıl bu bilgileri sıralanmış, gruplandırılmış ve döndürülmeden önce şeklinde belirtebilirsiniz. LINQ içinde bir sorgu bir değişkende depolanır. Bu sorgu değişkeni hiç eylem almaması ve veri döndürmemesidir; yalnızca, sorgu bilgileri depolar. Bir sorguyu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.  
  
 LINQ to Entities sorgularında iki farklı sözdizimini oluşan: sorgu ifadesi söz dizimi ve metot tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimi ve metot tabanlı sorgu söz dizimi, C# 3.0 ve Visual Basic 9.0 yenidir.  
  
 Daha fazla bilgi için [LINQ to Entities sorgularında](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Sorgu dönüştürme  
 Bir LINQ to Entities sorgusunda Entity Framework karşı yürütmek için LINQ sorgusu Entity Framework karşı yürütülen komut ağacı gösterimine dönüştürülmesi gerekir.  
  
 LINQ to Entities sorgularında LINQ standart sorgu işleçlerinin oluşan (gibi <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>, ve <xref:System.Linq.Queryable.GroupBy%2A>) ve ifadeler (x 10 >, Contact.LastName ve benzeri). LINQ işleçleri bir sınıf tarafından tanımlı değil, ancak bunun yerine bir sınıftaki olur. LINQ içinde ifade içindeki türleri tarafından izin verilen herhangi bir şey içerebilir <xref:System.Linq.Expressions> ad alanı ve bir lambda işlevi içinde gösterilen herhangi bir şey uzantısı. Bu veritabanı üzerinde izin verilen ve desteklediği işlemleri için kısıtlı tanımına göre olan Entity Framework tarafından izin verilen ifadeleri bir üst kümesidir <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Varlık Çerçevesi'nde hem işleçler ve ifadeler, ardından bir komut ağacındaki yerleştirilir bir tek tür hiyerarşisi tarafından gösterilir. Komut ağacı varlık çerçevesi tarafından sorguyu yürütmek için kullanılır. Sorgu dönüştürüldüğünde LINQ sorgusu bir komut ağacı ifade edilemediğinde bir özel durum oluşturulur. LINQ to Entities sorgularında dönüştürme iki alt dönüşümler içerir: Standart sorgu işleçlerinin dönüştürme ve ifadelerin dönüştürme.  
  
 Geçerli bir çeviri, LINQ to Entities'de olmayan LINQ standart sorgu işleçlerinin vardır. Bu işleçler kullanma girişimleri sorgu çevirisi zaman bir özel durum neden olur. Desteklenen LINQ to Entities işleçleri bir listesi için bkz. [desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 LINQ to Entities'de standart sorgu işleçlerini kullanma hakkında daha fazla bilgi için bkz. [LINQ to Entities sorgularında standart sorgu işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md).  
  
 Genel olarak, ifade davranışını CLR semantikleri izlemeyi beklendiği şekilde ifadeleri LINQ to Entities'de sunucusunda değerlendirilir. Daha fazla bilgi için [ifadeleri LINQ to Entities sorgularında](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
 CLR yöntem çağrılarını kurallı işlevler veri kaynağında nasıl eşlendiğine ilişkin daha fazla bilgi için bkz: [CLR yöntemini kurallı işlev eşleme Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
 Çağrı canonical, veritabanını ve özel işlevlerini LINQ to Entities sorgularında hakkında daha fazla bilgi için bkz. [LINQ to Entities sorgularında çağırma işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 LINQ sorgusu, kullanıcı tarafından oluşturulduktan sonra veri kaynağına karşı yürütülür Entity Framework (formunda komut ağaçlarının) ile uyumlu bir temsili dönüştürülür. Sorgu yürütme zamanında istemci veya sunucuda tüm sorgu ifadeleri (veya sorgunun bileşenleri) değerlendirilir. Bu sonuç materialization veya varlık projeksiyonlar kullanılan ifadeleri içerir. Daha fazla bilgi için [sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md). Bir sorgu kez derleyerek ve ardından farklı parametrelerle birkaç kez yürütme performansı hakkında daha fazla bilgi için bkz: [derlenmiş sorgular (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Gerçekleştirme  
 Materialization sorgu sonuçları CLR türleri olarak istemciye geri döndürülüyor işlemidir. İçinde bir LINQ to Entities sorgu sonuçları veri kayıtlarının hiçbir zaman verilir; her zaman kullanıcı veya Entity Framework tarafından tanımlanan veya (anonim türler) derleyici tarafından oluşturulan bir destekleyen CLR türünü yoktur. Tüm nesne gerçekleştirme, Entity Framework tarafından gerçekleştirilir. Entity Framework ve CLR arasında eşleştirilemez sonucunda herhangi bir hata özel durum sırasında nesne gerçekleştirme oluşturulmasına neden olur.  
  
 Sorgu sonuçları genellikle aşağıdakilerden biri döndürülür:  
  
- Sıfır veya daha fazla yazılan varlığın nesnelerin veya projeksiyon kavramsal modelde tanımlı karmaşık türleri koleksiyonu.  
  
- Tarafından desteklenen CLR türleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
- Satır içi koleksiyonları.  
  
- Anonim türler.  
  
 Daha fazla bilgi için [sorgu sonuçları](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
  
 [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)  
  
 [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
  
 [Derlenmiş Sorgular (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)  
  
 [Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)  
  
 [Sorgu Sonuçları](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)  
  
 [LINQ to Entities Sorgularında Standart Sorgu İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)  
  
 [CLR Yöntemini Kurallı İşlev ile Eşleme](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)  
  
 [Desteklenen ve Desteklenmeyen LINQ Yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
- [Dil ile tümleşik sorgu (LINQ)-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ ve ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
