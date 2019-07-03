---
title: Sorgu Sonuçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 165fb1524daa781c29037bf1c9cb2b3013504177
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539748"
---
# <a name="query-results"></a>Sorgu Sonuçları
Bir LINQ to Entities sorgusunda komut ağaçlarını dönüştürülür ve yürütülen sonra sorgu sonuçları genellikle aşağıdakilerden biri döndürülür:  
  
- Sıfır veya daha fazla yazılan bir varlığın nesnelerin veya projeksiyon kavramsal modeldeki karmaşık türleri koleksiyonu.  
  
- Kavramsal model tarafından desteklenen CLR türleri.  
  
- Satır içi koleksiyonları.  
  
- Anonim türler.  
  
 Veri kaynağına karşı sorgu yürütüldü, sonuç CLR türleriyle gerçekleştirilmiş ve istemciye döndürülen. Tüm nesne gerçekleştirme tarafından gerçekleştirilen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Eşleştirilemez arasında sonucunda herhangi bir hata [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ve CLR özel nesne gerçekleştirme sırasında durum oluşturulmasına neden olur.  
  
 Sorgu yürütme ilkel kavramsal model türü döndürürse, tek başına ve bağlantısı kesilmiş olan CLR türlerini sonuçları oluşur [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Sorgu yazılan varlığın nesnelerinin bir koleksiyonunu döndürür, ancak tarafından temsil edilen <xref:System.Data.Objects.ObjectQuery%601>, bu türleri nesne bağlamı tarafından izlenir. Tüm nesne davranışı (örneğin, alt/üst koleksiyonları, değişiklik izleme, çok biçimlilik ve benzeri) olan sınıfında tanımlandığı gibi [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Bu işlev, kapasitede sınıfında tanımlandığı gibi kullanılabilir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nesneleriyle çalışma](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Yapı türleri (örneğin anonim türler ve null olabilir karmaşık türler) sorgularından döndürülen olabilir `null` değeri. Bir <xref:System.Data.Objects.DataClasses.EntityCollection%601> döndürülen bir varlığın özelliği biri de olabilir `null` değeri. Bu, bir varlık koleksiyon özelliğini yansıtma gelen sonuçlanabilir `null` arama gibi değeri <xref:System.Linq.Queryable.FirstOrDefault%2A> üzerinde bir <xref:System.Data.Objects.ObjectQuery%601> , öğe yok.  
  
 Bazı durumlarda, bir sorgu yürütmesi sırasında gerçekleştirilmiş bir sonuç üretmek için görünebilir ancak sorgu sunucuda yürütülür ve varlık nesnesi hiçbir zaman CLR'de gerçekleştirilmiş. Nesne gerçekleştirme, yan etkileri bağlı, bu sorunlara neden olabilir.  
  
 Aşağıdaki örnek, özel bir sınıf içerir `MyContact`, ile bir `LastName` özelliği. Zaman `LastName` özelliği ayarlanmış bir `count` değişkeni artırılır. İki aşağıdaki sorguları yürütün, ilk sorgu artırır `count` karşın ikinci sorgu erişemez. Bunun nedeni, ikinci sorgu `LastName` özelliği sonuçlardan öngörülen ve `MyContact` sınıf hiçbir zaman oluşturulduğu, mağaza sorguyu yürütmek için gerekli olmadığından.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
