---
title: LINQ - Varlıklar
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: 7e04155c3129fd3b70977dd2960ccdc99c194cab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760784"
---
# <a name="linq-to-entities"></a>LINQ - Varlıklar
LINQ to Entities Visual Basic veya Visual C# kullanarak Entity Framework kavramsal model sorguları yazmaya geliştiricilerinin dil ile tümleşik sorgu (LINQ) desteği sağlar. Entity Framework sorguları karşı nesne bağlamı yürütme komut ağacı sorgular tarafından temsil edilir. LINQ to Entities ağaç sorgular, Entity Framework sorguları yürütür ve Entity Framework ve LINQ tarafından kullanılan nesneleri döndürür komut dil ile tümleşik sorgu (LINQ) sorguları dönüştürür. İşlem oluşturma ve bir LINQ to Entities sorgusunun yürütülmesi için aşağıdadır:  
  
1.  Oluşturmak bir <xref:System.Data.Objects.ObjectQuery%601> gelen örnek <xref:System.Data.Objects.ObjectContext>.  
  
2.  Kullanarak bir LINQ to Entities sorgusunda C# veya Visual Basic oluşturan <xref:System.Data.Objects.ObjectQuery%601> örneği.  
  
3.  LINQ standart sorgu işleçler ve ifadeler komut ağaçlarını dönüştürün.  
  
4.  Komut ağacı gösteriminde veri kaynağına karşı sorgu yürütün. Veri kaynağı üzerinde yürütme sırasında karşılaşılan özel durumlar doğrudan kadar istemci geçirilir.  
  
5.  Sorgu sonuçları istemciye geri dönün.  
  
## <a name="constructing-an-objectquery-instance"></a>Bir ObjectQuery örneğinin oluşturma  
 <xref:System.Data.Objects.ObjectQuery%601> Genel sınıfı, sıfır veya daha fazla yazılan varlıklar koleksiyonu döndüren bir sorgu temsil eder. Bir sorgu nesnesi bağlamından el ile yapılandırılan yerine var olan nesne, genellikle oluşturulur ve her zaman bu nesne bağlamına ait. Bu içerik oluşturabilir ve sorguyu yürütmek için gerekli meta veri bilgileri ve bağlantı sağlar. <xref:System.Data.Objects.ObjectQuery%601> Genel bir sınıf uygular <xref:System.Linq.IQueryable%601> olan oluşturucu yöntemleri LINQ sorgularını artımlı olarak oluşturulacak etkinleştirmek genel arabirim. Ayrıca C# kullanarak varlık türünü Infer derleyici sağlayabilirsiniz `var` anahtar sözcüğü (`Dim` etkin yerel türü çıkarımı ile Visual Basic'te).  
  
## <a name="composing-the-queries"></a>Sorgular oluşturma  
 Örneklerini <xref:System.Data.Objects.ObjectQuery%601> genel uygulayan genel sınıfı <xref:System.Linq.IQueryable%601> arabirim, veri kaynağı olarak Entities sorgularında LINQ hizmet. Sorgu içinde tam olarak veri kaynağından almak istediğiniz bilgileri belirtin. Bir sorgu de nasıl bu bilgileri sıralanmış, gruplandırılmış ve, döndürülmeden önce şeklinde belirtebilirsiniz. LINQ, sorgu bir değişkende depolanır. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve hiçbir veri döndürür; yalnızca, sorgu bilgileri depolar. Bir sorgu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.  
  
 LINQ to Entities sorgularında içinde iki farklı sözdizimi birleştirilebilen: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi. Sorgu ifade sözdizimi ve yöntem temelli sorgu söz dizimi, C# 3.0 ve Visual Basic 9.0 yenidir.  
  
 Daha fazla bilgi için bkz: [LINQ to Entities sorgularında](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Sorgu dönüştürme  
 Bir LINQ to Entities sorgusunda Entity Framework karşı çalıştırmak için Entity Framework karşı yürütülen komut ağacı gösterimi LINQ sorgusu dönüştürülmelidir.  
  
 LINQ to Entities sorgularında LINQ standart sorgu işleçleri oluşur (gibi <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>, ve <xref:System.Linq.Queryable.GroupBy%2A>) ve ifadeler (x > 10, Contact.LastName ve benzeri). LINQ işleçleri bir sınıf tarafından tanımlanan değil, ancak bunun yerine bir sınıftaki yöntemleri şunlardır. LINQ, içinde türleri tarafından izin verilen herhangi bir şey ifadeleri içeren <xref:System.Linq.Expressions> ad alanı ve bir lambda işlevinde temsil edilebilir herhangi bir şey uzantısı. Bu veritabanı üzerinde izin verilen ve tarafından desteklenen operations sınırlı tanımı tarafından olan Entity Framework tarafından izin verilen ifadeleri bir üst kümesidir <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Entity Framework işleçler ve ifadeler tek türü hiyerarşisi tarafından bir komut ağacındaki sonra yerleştirilir gösterilir. Komut ağacı Entity Framework tarafından sorguyu yürütmek için kullanılır. LINQ Sorgu komut ağacı ile açıklanamayan, sorgu dönüştürüldüğünde bir özel durum. İki alt dönüşümleri Entities sorgularında LINQ dönüştürülmesi içerir: Standart sorgu işleçleri dönüştürülmesi ve dönüştürme bir ifade.  
  
 LINQ to Entities içinde geçerli bir çeviri yok LINQ standart sorgu işleçleri mevcuttur. Bu işleçlere kullanma girişimleri bir özel durum sorgusu çevirisi zaman neden olur. Desteklenen LINQ to Entities işleçleri listesi için bkz: [desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 LINQ to Entities içinde standart sorgu işleçleri kullanma hakkında daha fazla bilgi için bkz: [LINQ to Entities sorgularında standart sorgu işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md).  
  
 Genel olarak, ifade davranışını CLR semantikleri izlemeyi beklendiği şekilde ifadeler LINQ to Entities içinde sunucu üzerinde değerlendirilir. Daha fazla bilgi için bkz: [LINQ to Entities sorgu ifadelerinde](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
 CLR yöntem çağrılarını veri kaynağındaki kurallı işlevleri nasıl eşlendiği hakkında daha fazla bilgi için bkz: [kurallı işlev eşleme CLR yönteme](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
 Kurallı çağırmak üzere, veritabanı ve içinden özel işlevler hakkında bilgi için [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları, bkz: [çağırma işlevleri LINQ to Entities sorgularında](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 LINQ Sorgu kullanıcı tarafından oluşturulduktan sonra ardından veri kaynağında yürütülen Entity Framework (biçiminde komut ağaçlarını), ile uyumlu bir gösterimi dönüştürülür. Sorgu yürütme sırasında tüm sorgu ifadeleri (veya sorgu bileşenlerinin) istemci veya sunucuda değerlendirilir. Bu, kullanılan ifadeler sonuç materialization veya varlık projeksiyonları içerir. Daha fazla bilgi için bkz: [sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md). Bir sorgu kez derleme ve ardından farklı parametrelerle birkaç kez çalıştırma performansı hakkında daha fazla bilgi için bkz: [derlenmiş sorgu (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Materialization  
 Materialization sorgu sonuçları CLR türleri olarak istemciye geri döndürülüyor işlemidir. İçinde bir LINQ to Entities sorgu sonuçları veri kayıtlarını hiçbir zaman verilir; her zaman kullanıcı tarafından veya Entity Framework tarafından tanımlanan veya (anonim türler) derleyici tarafından üretilen bir destekleyen CLR türü yok. Tüm nesne materialization Entity Framework tarafından gerçekleştirilir. Entity Framework CLR arasında eşleştirilemez kaynaklanan hataları sırasında nesne materialization durum için özel durumlar neden olur.  
  
 Sorgu sonuçları genellikle aşağıdakilerden biri döndürülen:  
  
-   Sıfır veya daha fazla belirtilmiş varlık nesnesi ya da projeksiyon, kavramsal modelde tanımlanan karmaşık türler koleksiyonu.  
  
-   Tarafından desteklenen CLR türleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
-   Satır içi koleksiyonları.  
  
-   Anonim türler.  
  
 Daha fazla bilgi için bkz: [sorgu sonuçları](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ ve ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
