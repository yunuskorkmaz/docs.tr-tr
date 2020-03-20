---
title: Derlenmiş Sorgular (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 97ceef3377a67fc621a097843abade9c61c29ca1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848775"
---
# <a name="compiled-queries--linq-to-entities"></a>Derlenmiş Sorgular (LINQ to Entities)
Varlık Çerçevesi'nde yapısal olarak benzer sorguları birçok kez yürüten bir uygulamanız olduğunda, sorguyu bir kez derleyerek ve farklı parametrelerle birkaç kez çalıştırarak performansı sık sık artırabilirsiniz. Örneğin, bir uygulamanın belirli bir şehirdeki tüm müşterileri alması gerekebilir; şehir bir formda kullanıcı tarafından çalışma zamanında belirtilir. LINQ to Varlıklar, bu amaçla derlenmiş sorguları kullanmayı destekler.  
  
 .NET Framework 4.5 ile başlayarak LINQ sorguları otomatik olarak önbelleğe alınır. Ancak, daha sonraki yürütmelerde bu maliyeti azaltmak için derlenmiş LINQ sorgularını kullanmaya devam edebilirsiniz ve derlenen sorgular otomatik olarak önbelleğe alınmış LINQ sorgularından daha verimli olabilir. `Enumerable.Contains` İşleçteni bellek içi koleksiyonlara uygulayan VARLıKLARa LINQ sorgularının otomatik olarak önbelleğe alınmadığını unutmayın. Ayrıca derlenmiş LINQ sorgularında bellek içi koleksiyonları parametrelendirmeye izin verilmez.  
  
 Sınıf, <xref:System.Data.Objects.CompiledQuery> yeniden kullanmak için sorguların derlemisini ve önbelleğe alınmış kısmını sağlar. Kavramsal olarak, bu <xref:System.Data.Objects.CompiledQuery>sınıf `Compile` birkaç aşırı yükleme içeren bir 's yöntemi içerir. Derlenen `Compile` sorguyu temsil edecek yeni bir temsilci oluşturmak için yöntemi çağırın. A `Compile` <xref:System.Data.Objects.ObjectContext> ve parametre değerleriyle sağlanan yöntemler, bazı sonuçlar (örneğin) <xref:System.Linq.IQueryable%601> üreten bir temsilci döndürür. Sorgu yalnızca ilk yürütme sırasında bir kez derler. Derleme sırasında sorgu için ayarlanan birleştirme seçenekleri daha sonra değiştirilemez. Sorgu derlendikten sonra yalnızca ilkel türparametreleri sağlayabilirsiniz, ancak sorgunun oluşturulan SQL'i değiştirecek bölümlerini değiştiremezsiniz. Daha fazla bilgi [için, EF Birleştirme Seçenekleri ve Derlenmiş Sorgular'a](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)bakın.
  
 <xref:System.Data.Objects.CompiledQuery>'ın `Compile` derletir dediği LINQ- Varlıklar sorgu ifadesi, `Func` <xref:System.Func%605>genel temsilcilerden biri tarafından temsil edilir. En fazla, sorgu ifadesi bir `ObjectContext` parametre, bir dönüş parametresi ve 16 sorgu parametrelerini kapsülleyebilir. 16'dan fazla sorgu parametresi gerekiyorsa, özellikleri sorgu parametrelerini temsil eden bir yapı oluşturabilirsiniz. Daha sonra özellikleri ayarladıktan sonra sorgu ifadesinde yapı daki özellikleri kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, giriş <xref:System.Decimal> parametresini kabul eden ve vadesi gelen toplamın 200,00 TL'den büyük veya eşit olduğu bir sipariş dizisi döndüren bir sorgu yuvarlanır ve çağırır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve sonra bir <xref:System.Data.Objects.ObjectQuery%601> örnek döndürür bir sorgu çağırır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve sonra ürün listesi fiyatlarının ortalamasını bir <xref:System.Decimal> değer olarak döndüren bir sorgu çağırır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve sonra bir giriş <xref:System.String> parametresi kabul eden `Contact` bir sorgu çağırır ve sonra belirtilen dize ile başlayan bir e-posta adresi döndürür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, parametreleri kabul <xref:System.DateTime> eden ve <xref:System.Decimal> girdi sağlayan bir sorguyu derler ve çağırır ve sipariş tarihinin 8 Mart 2003'ten sonra olduğu ve vadesi 300,00 TL'den az olan bir sipariş dizisi döndürür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, giriş parametresini kabul eden <xref:System.DateTime> ve sipariş tarihinin 8 Mart 2004'ten sonra olduğu bir sipariş sırasını döndüren bir sorgu yuder ve çağırır. Bu sorgu, sipariş bilgilerini anonim türler dizisi olarak döndürür. Anonim türler derleyici tarafından çıkarılır, bu nedenle <xref:System.Data.Objects.CompiledQuery>'ın `Compile` yönteminde tür parametreleri belirtemezsiniz ve tür sorgunun kendisinde tanımlanır.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve sonra kullanıcı tanımlı yapı giriş parametresi kabul eden ve bir sipariş dizisi döndüren bir sorgu çağırır. Yapı başlangıç tarihi, bitiş tarihi ve toplam vade sorgusu parametrelerini tanımlar ve sorgu, 3 Mart ile 8 Mart 2003 tarihleri arasında gönderilen siparişleri toplam vadesi 700,00 TL'den fazla olan siparişleri döndürür.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Sorgu parametrelerini tanımlayan yapı:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../index.md)
- [LINQ - Varlıklar](linq-to-entities.md)
- [EF Birleştirme Seçenekleri ve Derlenmiş Sorgular](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
