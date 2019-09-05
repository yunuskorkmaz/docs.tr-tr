---
title: LINQ - Varlıklar
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: bdc93b609dd88449308508bf88635cc706d91e64
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250401"
---
# <a name="linq-to-entities"></a>LINQ - Varlıklar
LINQ to Entities, geliştiricilerin Visual Basic veya görseli C#kullanarak Entity Framework kavramsal modele yönelik sorgular yazmasını sağlayan dil Ile tümleşik sorgu (LINQ) desteği sağlar. Entity Framework yapılan sorgular, nesne bağlamına göre yürütülen komut ağacı sorgularıyla temsil edilir. LINQ to Entities, dil ile tümleşik sorgular (LINQ) sorgularını komut ağacı sorgularına dönüştürür, sorguları Entity Framework yürütür ve hem Entity Framework hem de LINQ tarafından kullanılabilecek nesneleri döndürür. LINQ to Entities bir sorgu oluşturma ve yürütme süreci aşağıda verilmiştir:  
  
1. <xref:System.Data.Objects.ObjectQuery%601> Öğesinden<xref:System.Data.Objects.ObjectContext>bir örnek oluşturun.  
  
2. <xref:System.Data.Objects.ObjectQuery%601> Örneği kullanarak veya Visual Basic içinde C# LINQ to Entities bir sorgu oluşturun.  
  
3. LINQ standart sorgu işleçlerini ve ifadelerini komut ağaçlarına Dönüştür.  
  
4. Sorguyu, komut ağacı gösteriminde, veri kaynağına karşı yürütün. Yürütme sırasında veri kaynağında oluşan tüm özel durumlar doğrudan istemciye geçirilir.  
  
5. Sorgu sonuçlarını istemciye geri döndürün.  
  
## <a name="constructing-an-objectquery-instance"></a>ObjectQuery örneği oluşturma  
 Genel <xref:System.Data.Objects.ObjectQuery%601> sınıf, sıfır veya daha fazla türü belirtilmiş varlıkların koleksiyonunu döndüren bir sorguyu temsil eder. Bir nesne sorgusu, genellikle el ile oluşturulması yerine var olan bir nesne bağlamından oluşturulur ve bu nesne bağlamına her zaman aittir. Bu bağlam, sorguyu oluşturmak ve yürütmek için gerekli olan bağlantı ve meta veri bilgilerini sağlar. Genel sınıf, Oluşturucu yöntemleri <xref:System.Linq.IQueryable%601> LINQ sorgularının artımlı olarak derlenme özelliğini etkinleştiren genel arabirimini uygular. <xref:System.Data.Objects.ObjectQuery%601> Ayrıca derleyicinin, C# `var` anahtar sözcüğünü kullanarak varlık türünü (`Dim` Visual Basic, yerel tür çıkarımı etkinken) çıkarmasına izin verebilirsiniz.  
  
## <a name="composing-the-queries"></a>Sorguları oluşturma  
 Genel arabirimi<xref:System.Linq.IQueryable%601> uygulayan genelsınıfınörnekleri,LINQtoEntitiessorgularıiçinverikaynağıolarakgörevyapar.<xref:System.Data.Objects.ObjectQuery%601> Bir sorguda, tam olarak veri kaynağından almak istediğiniz bilgileri belirtirsiniz. Bir sorgu, döndürülmeden önce bu bilgilerin nasıl sıralanacağını, gruplanacağını ve şekillendirilmiş olduğunu da belirtebilir. LINQ içinde, bir sorgu bir değişkende depolanır. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve veri döndürmez; yalnızca sorgu bilgilerini depolar. Bir sorgu oluşturduktan sonra, verileri almak için bu sorguyu yürütmeniz gerekir.  
  
 LINQ to Entities sorguları iki farklı Sözdizimde olabilir: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimi ve Yöntem tabanlı sorgu söz dizimi 3,0 ve C# Visual Basic 9,0 ' de yenidir.  
  
 Daha fazla bilgi için bkz. [LINQ to Entities sorguları](queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Sorgu dönüştürme  
 Entity Framework karşı LINQ to Entities bir sorgu yürütmek için, LINQ sorgusunun Entity Framework karşı yürütülebilecek bir komut ağacı gösterimine dönüştürülmesi gerekir.  
  
 LINQ to Entities sorguları LINQ standart sorgu işleçlerinden (örneğin <xref:System.Linq.Queryable.Select%2A> <xref:System.Linq.Queryable.Where%2A>,, ve <xref:System.Linq.Queryable.GroupBy%2A>) ve ifadeler (x > 10, Contact. LastName, vb.) oluşur. LINQ işleçleri bir sınıf tarafından tanımlanmamıştır, ancak bunun yerine bir sınıf üzerinde yöntemler vardır. LINQ içinde, ifadeler <xref:System.Linq.Expressions> ad alanındaki türlerin izin verdiği herhangi bir şeyi ve uzantıya göre, bir lambda işlevinde temsil edilebilir her şeyi içerebilir. Bu, tanım tarafından veritabanında izin verilen işlemlere kısıtlanmış ve tarafından <xref:System.Data.Objects.ObjectQuery%601>desteklenen Entity Framework izin verilen ifadelerin bir üst kümesidir.  
  
 Entity Framework, her iki işleç ve ifade, bir komut ağacına yerleştirilmiş olan tek bir tür hiyerarşisi tarafından temsil edilir. Komut ağacı, sorguyu yürütmek için Entity Framework tarafından kullanılır. LINQ sorgusu bir komut ağacı olarak ifade edilemiyorsa, sorgu dönüştürülürken bir özel durum oluşturulur. LINQ to Entities sorgularının dönüştürülmesi iki alt dönüştürme içerir: standart sorgu işleçleri dönüştürme ve ifadelerin dönüştürülmesi.  
  
 LINQ to Entities içinde geçerli bir çeviriye sahip olmayan bir dizi LINQ standart sorgu işleci vardır. Bu işleçleri kullanma girişimleri, sorgu çevirisi zamanında bir özel durumla sonuçlanır. Desteklenen LINQ to Entities işleçleri listesi için bkz. [desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 LINQ to Entities 'de standart sorgu işleçlerini kullanma hakkında daha fazla bilgi için, bkz. [LINQ to Entities sorgularda standart sorgu işleçleri](standard-query-operators-in-linq-to-entities-queries.md).  
  
 Genel olarak, LINQ to Entities ifadeleri sunucuda değerlendirilir, bu nedenle ifadenin davranışının CLR semantiğini izlemesi beklenmemelidir. Daha fazla bilgi için bkz. [LINQ to Entities sorgulardaki ifadeler](expressions-in-linq-to-entities-queries.md).  
  
 CLR yöntemi çağrılarının veri kaynağında kurallı işlevlere nasıl eşlenildiği hakkında bilgi için bkz. [clr Method to kurallı Işlev eşlemesi](clr-method-to-canonical-function-mapping.md).  
  
 LINQ to Entities sorguların içinden kurallı, veritabanı ve özel işlevleri çağırma hakkında daha fazla bilgi için bkz. [LINQ to Entities sorgularda Işlevleri çağırma](calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 LINQ sorgusu Kullanıcı tarafından oluşturulduktan sonra, bu, daha sonra veri kaynağında yürütülen Entity Framework (komut ağaçları biçiminde) ile uyumlu bir gösterimine dönüştürülür. Sorgu yürütme sırasında, istemci veya sunucu üzerinde tüm sorgu ifadeleri (veya sorgunun bileşenleri) değerlendirilir. Bu, sonuç gerçekleştirmesi veya varlık projeksiyonde kullanılan ifadeleri içerir. Daha fazla bilgi için bkz. [sorgu yürütme](query-execution.md). Bir sorguyu bir kez derleyip daha sonra farklı parametrelerle birkaç kez yürütürken performansı geliştirme hakkında daha fazla bilgi için bkz. [derlenmiş sorgular (LINQ to Entities)](compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Gerçekleştirmesi  
 Materialization, sorgu sonuçlarının istemciye CLR türleri olarak geri döndürülmesi işlemidir. LINQ to Entities, sorgu sonuçları veri kayıtları hiçbir şekilde döndürülmez; Kullanıcı tarafından veya Entity Framework tarafından tanımlanan veya derleyici (anonim türler) tarafından oluşturulan bir destek CLR türü her zaman vardır. Tüm nesne gerçekleştirmesi Entity Framework tarafından gerçekleştirilir. Entity Framework ile CLR arasında eşleme yapılmamasına neden olan hatalar, nesne materialization sırasında özel durumların oluşturulmasına neden olur.  
  
 Sorgu sonuçları genellikle aşağıdakilerden biri olarak döndürülür:  
  
- Sıfır veya daha fazla yazılmış varlık nesnesi koleksiyonu veya kavramsal modelde tanımlanan karmaşık türlerin bir kümesi.  
  
- Tarafından desteklenen CLR türleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
- Satır içi Koleksiyonlar.  
  
- Anonim türler.  
  
 Daha fazla bilgi için bkz. [sorgu sonuçları](query-results.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)  
  
 [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)  
  
 [LINQ to Entities Sorgularında Çağırma İşlevleri](calling-functions-in-linq-to-entities-queries.md)  
  
 [Derlenmiş Sorgular (LINQ to Entities)](compiled-queries-linq-to-entities.md)  
  
 [Sorgu Yürütme](query-execution.md)  
  
 [Sorgu Sonuçları](query-results.md)  
  
 [LINQ to Entities Sorgularında Standart Sorgu İşleçleri](standard-query-operators-in-linq-to-entities-queries.md)  
  
 [CLR Yöntemini Kurallı İşlev ile Eşleme](clr-method-to-canonical-function-mapping.md)  
  
 [Desteklenen ve Desteklenmeyen LINQ Yöntemleri (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](known-issues-and-considerations-in-linq-to-entities.md)
- [Dil ile tümleşik sorgu (LINQ)-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ ve ADO.NET](../../linq-and-ado-net.md)
- [ADO.NET Entity Framework](../index.md)
