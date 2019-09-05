---
title: Sorgu Sonuçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: d43ec0cdf5b5bb03854dffc7132dddb4c9ae76fd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249262"
---
# <a name="query-results"></a>Sorgu Sonuçları
Bir LINQ to Entities sorgusu komut ağaçlarına dönüştürüldükten ve yürütüldükten sonra sorgu sonuçları genellikle aşağıdakilerden biri olarak döndürülür:  
  
- Sıfır veya daha fazla yazılmış varlık nesnesi koleksiyonu veya kavramsal modeldeki karmaşık türlerin bir projeksiyonu.  
  
- Kavramsal model tarafından desteklenen CLR türleri.  
  
- Satır içi Koleksiyonlar.  
  
- Anonim türler.  
  
 Sorgu veri kaynağına karşı yürütüldüğünde, sonuçlar CLR türlerine getirilir ve istemciye döndürülür. Tüm nesne gerçekleştirmesi, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]tarafından gerçekleştirilir. İle clr arasında eşleme yapılmamasına neden olan herhangi bir hata [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] , nesne materialization sırasında özel durumların oluşturulmasına neden olur.  
  
 Sorgu yürütmesi basit kavramsal model türleri döndürürse, sonuçlar tek başına olan ve bağlantısı kesilen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]CLR türlerinden oluşur. Ancak sorgu, türü ile <xref:System.Data.Objects.ObjectQuery%601>temsil edilen bir tür varlık nesneleri koleksiyonu döndürürse, bu türler nesne bağlamı tarafından izlenir. Tüm nesne davranışları (alt/üst koleksiyonlar, değişiklik izleme, çok biçimlilik vb [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].) içinde tanımlanmıştır. Bu işlev, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]içinde tanımlandığı şekilde kapasitesinde kullanılabilir. Daha fazla bilgi için bkz. [nesneleriyle çalışma](../working-with-objects.md).  
  
 Sorgulardan döndürülen yapı türleri (anonim türler ve null yapılabilir karmaşık türler gibi) `null` değer olabilir. Döndürülen <xref:System.Data.Objects.DataClasses.EntityCollection%601> bir varlığın özelliği de bir `null` değer olabilir. Bu, herhangi bir öğeye sahip olmayan bir `null` <xref:System.Data.Objects.ObjectQuery%601> ' ın çağrılması <xref:System.Linq.Queryable.FirstOrDefault%2A> gibi, değer olan bir varlığın koleksiyon özelliğinin yansıtıyapılmasının oluşmasına neden olabilir.  
  
 Belirli durumlarda, yürütme sırasında gerçekleştirilmiş sonuç oluşturmak için bir sorgu görünebilir, ancak sorgu sunucuda yürütülecektir ve varlık nesnesi hiçbir şekilde CLR 'de gerçekleştirilmeyecektir. Bu, nesne materialization 'in yan etkileriyle ilgili olarak sorun oluşmasına neden olabilir.  
  
 Aşağıdaki örnek, `LastName` özelliği ile özel bir sınıfı `MyContact`içerir. Özellik ayarlandığında, bir `count` değişken artırılır. `LastName` Aşağıdaki iki sorguyu çalıştırırsanız, ikinci sorgu bu sırada ilk sorgu artacaktır `count` . Bunun nedeni, ikinci sorgudaki `LastName` özelliğin sonuçlardan yansıtıldığı `MyContact` ve sınıfın depoda hiçbir şekilde oluşturulamadığından, sorgunun mağazada yürütülmesi gerekmediği için değildir.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
