---
title: Derlenmiş sorgular (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 362ba0000c739c8fc216186514a63531e603c637
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502027"
---
# <a name="compiled-queries--linq-to-entities"></a>Derlenmiş sorgular (LINQ to Entities)
Birden çok kez varlık Çerçevesi'nde yapısal olarak benzer sorguları yürüten bir uygulamanız varsa, sorgu bir kez derleyerek ve birkaç kez farklı parametrelerle yürütme sık performansı artırabilirsiniz. Örneğin, bir uygulama belirli bir şehirdeki tüm müşterileri alma gerekebilir; Şehir, çalışma zamanında bir forma kullanıcı tarafından belirtilir. LINQ to Entities, bu amaç için derlenmiş sorgular kullanmayı destekler.  
  
 .NET Framework 4.5 ile başlayarak, LINQ sorguları otomatik olarak önbelleğe. Ancak, bu sonraki yürütme sayısı maliyeti azaltmak için derlenmiş LINQ sorguları kullanmaya devam edebilirsiniz ve derlenmiş sorgular otomatik olarak önbelleğe LINQ sorguları daha verimli olabilir. LINQ to Entities sorguları Not geçerli `Enumerable.Contains` işleci bellek içi koleksiyonlara otomatik olarak önbelleğe alınmaz. Bellek içi koleksiyonları derlenmiş LINQ sorgularında ayrıca kümesini parametreleştirme izin verilmez.  
  
 <xref:System.Data.Objects.CompiledQuery> Sınıfı, derleme ve sorguları yeniden kullanım için önbelleğe alınmasını sağlar. Kavramsal olarak, bu sınıf içeren bir <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi ile çeşitli aşırı yükler. Çağrı `Compile` derlenmiş sorguyu temsil etmek için yeni bir temsilci oluşturmak için yöntemi. `Compile` İle sağlanan yöntemleri, bir <xref:System.Data.Objects.ObjectContext> ve bazı sonucu üreten bir temsilci dönüş parametresi değerleri (gibi bir <xref:System.Linq.IQueryable%601> örnek). Sorgu bir kez yalnızca ilk yürütme sırasında derler. Sorgu için derleme ayarlarken birleştirme seçeneklerini daha sonra değiştirilemez. Sorgu derlenmiş sonra yalnızca ilkel tür parametrelerinin sağlayabilirsiniz, ancak oluşturulan SQL değiştirirsiniz sorgunun bölümlerini değiştirilemiyor. Daha fazla bilgi için [Entity Framework birleştirme seçeneklerini ve derlenmiş sorgular](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Sorgu ifadesi, <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi derler genel biri tarafından temsil edilir `Func` gibi Temsilciler <xref:System.Func%605>. En fazla sorgu ifadesi kapsülleyebilir bir `ObjectContext` parametre, dönüş parametresi ve 16 sorgu parametreleri. 16'dan fazla sorgu parametreleri gerekiyorsa, sorgu parametreleri özelliklerini temsil eden bir yapı oluşturabilirsiniz. Özellikler ayarlandıktan sonra sorgu ifadesinde yapısına özelliklerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve ardından kabul eden bir sorguyu çağırır bir <xref:System.Decimal> giriş parametresi ve toplam süre değerinden büyük veya eşittir $200,00 olduğu siparişler bir dizi döndürür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve ardından döndüren bir sorgu çağıran bir <xref:System.Data.Objects.ObjectQuery%601> örneği:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve daha sonra ürün listesi fiyatlar ortalamasını döndüren bir sorgu çalıştırır bir <xref:System.Decimal> değeri:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve ardından kabul eden bir sorguyu çağırır bir <xref:System.String> giriş parametresi ve döndürür bir `Contact` , e-posta adresi belirtilen dize ile başlar:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve ardından kabul eden bir sorguyu çağırır <xref:System.DateTime> ve <xref:System.Decimal> küçüktür $300.00 olan giriş parametreleri ve bir dizi, sipariş tarihi 8 Mart 2003'ten daha sonra olduğu ve son toplam siparişleri döndürür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve ardından kabul eden bir sorguyu çağırır bir <xref:System.DateTime> giriş parametresi ve sipariş tarihi 8 Mart 2004 ' sonraki olduğu siparişler bir dizisini döndürür. Bu sorgu, anonim türdeki sipariş bilgileri bir dizisi olarak döndürür. Anonim türler tür parametrelerinde belirtemezsiniz derleyici tarafından çıkarılan <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi ve türü sorguda tanımlanır.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve ardından, kullanıcı tanımlı yapısı giriş parametresi kabul eden ve siparişlerinin bir dizi döndürür bir sorgu çalıştırır. Başlangıç tarihi, bitiş tarihi ve toplam sorgu parametreleri nedeniyle yapısını tanımlar ve Mart 3 ve 8 Mart 2003 toplam $700.00 büyüktür son siparişlere sorguyu döndürür.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Sorgu parametrelerini tanımlayan yapısı:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Entity Framework birleştirme seçeneklerini ve derlenmiş sorgular](https://go.microsoft.com/fwlink/?LinkId=199591)
