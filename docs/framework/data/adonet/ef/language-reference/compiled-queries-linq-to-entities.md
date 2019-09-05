---
title: Derlenmiş Sorgular (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 2d9df4d479605c0a2514fe30a9150ab7bcfe904e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251164"
---
# <a name="compiled-queries--linq-to-entities"></a>Derlenmiş Sorgular (LINQ to Entities)
Entity Framework birden çok kez yapısal olarak benzer sorgular yürüten bir uygulamanız varsa, sorguyu bir kez derleyerek ve farklı parametrelerle birkaç kez yürüterek performansı sıklıkla artırabilirsiniz. Örneğin, bir uygulama belirli bir şehirdeki tüm müşterileri almak zorunda kalabilir. Şehir, çalışma zamanında Kullanıcı tarafından bir formda belirtilir. LINQ to Entities, bu amaçla derlenen sorguların kullanılmasını destekler.  
  
 .NET Framework 4,5 ' den başlayarak LINQ sorguları otomatik olarak önbelleğe alınır. Ancak, daha sonra yürütmelerin ve derlenmiş sorguların bu maliyeti azaltmak için derlenen LINQ sorgularını kullanmaya devam edebilirsiniz. bu da, otomatik olarak önbelleğe alınan LINQ sorgularından daha verimli olabilir. Bu işleci, `Enumerable.Contains` bellek içi koleksiyonlara uygulayan LINQ to Entities sorgularının otomatik olarak önbelleğe alınmadığını unutmayın. Ayrıca, derlenen LINQ sorgularında bellek içi koleksiyonlara parametreleştirmeye izin verilmez.  
  
 Sınıfı <xref:System.Data.Objects.CompiledQuery> , yeniden kullanım için sorguları derleme ve önbelleğe alma sağlar. Kavramsal olarak, bu sınıf birkaç <xref:System.Data.Objects.CompiledQuery>aşırı `Compile` yükleme içeren bir yöntemi içerir. Derlenen sorguyu temsil etmek üzere yeni bir temsilci oluşturmak için yönteminiçağırın.`Compile` <xref:System.Data.Objects.ObjectContext> <xref:System.Linq.IQueryable%601> Ve parametre değerleriyle birlikte sunulan Yöntemler,bazısonuçlarüretenbirtemsilcidöndürür(örneğin,birörnek).`Compile` Sorgu yalnızca ilk yürütme sırasında bir kez derlenir. Derleme sırasında sorgu için ayarlanan birleştirme seçenekleri daha sonra değiştirilemez. Sorgu derlendikten sonra yalnızca temel tür parametreleri sağlayabilirsiniz ancak oluşturulan SQL 'yi değiştirecek sorgunun parçalarını değiştiremezsiniz. Daha fazla bilgi için bkz. [Entity Framework birleştirme seçenekleri ve derlenmiş sorgular](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 Yöntemi derleyen LINQ to Entities sorgu ifadesi <xref:System.Data.Objects.CompiledQuery> `Func` <xref:System.Func%605>, genel temsilcilerden biri (gibi) ile temsil edilir. `Compile` En çok, sorgu ifadesi bir `ObjectContext` parametreyi, dönüş parametresini ve 16 sorgu parametresini kapsülleyebilirsiniz. 16 ' dan fazla sorgu parametresi gerekliyse, özellikleri sorgu parametrelerini temsil eden bir yapı oluşturabilirsiniz. Daha sonra özellikleri ayarladıktan sonra sorgu ifadesindeki yapıda özellikleri kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Decimal> giriş parametresi kabul eden bir sorgu çağırır ve sonra, ödenecek toplam değer $200,00 ' den büyük veya buna eşit olan bir sipariş dizisi döndürür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Data.Objects.ObjectQuery%601> örnek döndüren bir sorgu derler ve çağırır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ürün listesi fiyatlarının ortalamasını bir <xref:System.Decimal> değer olarak döndüren bir sorguyu derler ve çağırır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.String> giriş parametresi kabul eden bir sorguyu derler ve sonra bir e-posta adresinin belirtilen dizeyle başladığı bir `Contact` sorgu çağırır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, parametreleri kabul <xref:System.DateTime> eden ve <xref:System.Decimal> giriş yapan bir sorgu çağırır ve sonra sipariş tarihinin 8 Mart 2003 ' den daha geç olduğu ve süresi $300,00 ' den küçük olan bir sıra dizisi döndürüyor:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.DateTime> giriş parametresi kabul eden bir sorgu çağırır ve sonra sipariş tarihinin 8 Mart 2004 ' den sonraki bir sıra sırasını döndürür. Bu sorgu, düzen bilgilerini anonim türlerin bir dizisi olarak döndürür. Anonim türler derleyici tarafından algılanır, bu nedenle <xref:System.Data.Objects.CompiledQuery>kendi `Compile` yönteminde tür parametreleri belirtemezsiniz ve tür sorgunun kendisinde tanımlanmış.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Kullanıcı tanımlı bir yapı giriş parametresini kabul eden ve bir dizi siparişi döndüren bir sorguyu derler ve çağırır. Yapı başlangıç tarihi, bitiş tarihi ve toplam son sorgu parametresini tanımlar ve sorgu, $700,00 Mart 3 ve 8 Mart 2003 tarihleri arasında, ' den büyük bir süre ile gönderilen siparişleri döndürür.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Sorgu parametrelerini tanımlayan yapı:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../index.md)
- [LINQ to Entities](linq-to-entities.md)
- [Entity Framework birleştirme seçenekleri ve derlenmiş sorgular](https://go.microsoft.com/fwlink/?LinkId=199591)
