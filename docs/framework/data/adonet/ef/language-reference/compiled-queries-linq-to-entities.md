---
title: "Derlenmiş sorgu (LINQ to Entities)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4cdea4d0ca5a8f7b829b9d0a99a6097d164bbf21
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="compiled-queries--linq-to-entities"></a>Derlenmiş sorgu (LINQ to Entities)
Entity Framework içinde birçok kez yapısal olarak benzer sorguları yürüten bir uygulamanız varsa, bir kez sorgu derleme ve farklı parametrelerle birkaç kez yürütme tarafından sık performansını artırabilirsiniz. Örneğin, belirli bir şehirde tüm müşteriler almak bir uygulama olabilir; Şehir çalışma zamanında bir form kullanıcı tarafından belirtilir. LINQ to Entities bu amaç için derlenmiş sorgularını kullanarak destekler.  
  
 .NET Framework 4. 5'ile başlayarak, LINQ sorgularını otomatik olarak önbelleğe. Ancak, sonraki yürütmeleri içinde bu maliyetini azaltmak için derlenmiş LINQ sorgularını kullanmaya devam edebilirsiniz ve derlenmiş sorguları otomatik olarak önbelleğe alınan LINQ sorgularını daha etkili olabilir. LINQ to Entities sorguları Not geçerli `Enumerable.Contains` bellek içi koleksiyonlara işleci otomatik olarak önbelleğe alınmaz. Ayrıca derlenmiş LINQ sorgularını bellek içi koleksiyonlarda kümesini parametreleştirme izin verilmiyor.  
  
 <xref:System.Data.Objects.CompiledQuery> Sınıfı, derleme ve yeniden kullanım için sorguları önbelleğe alınmasını sağlar. Kavramsal olarak, bu sınıfı içeren bir <xref:System.Data.Objects.CompiledQuery>'s `Compile` birkaç aşırı yöntemiyle. Çağrı `Compile` derlenmiş sorgu temsil etmek için yeni bir temsilci oluşturmak için yöntemi. `Compile` İle sağlanan yöntemleri, bir <xref:System.Data.Objects.ObjectContext> ve bazı sonuç üreten bir temsilci dönüş parametre değerleri (gibi bir <xref:System.Linq.IQueryable%601> örnek). Sorgu bir kez yalnızca ilk yürütme sırasında derler. Sorgu için derleme zamanında ayarlamak birleştirme seçeneklerini daha sonra değiştirilemez. Sorgu derlenmiş sonra yalnızca ilkel tür parametrelerinin sağlayabilir ancak oluşturulan SQL değişeceğinden sorgunun bölümlerini değiştirilemiyor. Daha fazla bilgi için bkz: [Entity Framework birleştirme seçenekleri ve derlenmiş sorguları](http://go.microsoft.com/fwlink/?LinkId=199591)  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Sorgu ifadesi, <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi derlerken genel biri tarafından temsil edilir `Func` gibi Temsilciler <xref:System.Func%605>. Sorgu ifadesi en fazla sarmalayabilen bir `ObjectContext` parametresi, bir dönüş parametresi ve 16 sorgu parametreleri. 16'dan fazla sorgu parametreleri gerekirse, sorgu parametreleri özellikleri temsil eden bir yapı oluşturabilirsiniz. Özellikler ayarlandıktan sonra sorgu ifadesinde yapısına özelliklerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve kabul eden bir sorgu çağıran bir <xref:System.Decimal> giriş parametresi ve toplam süre $200,00 eşit veya daha büyük olduğu siparişler bir dizi döndürür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve döndüren bir sorgu çağıran bir <xref:System.Data.Objects.ObjectQuery%601> örneği:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve ürün listesi fiyatlar ortalaması döndüren bir sorgu çağıran bir <xref:System.Decimal> değeri:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve kabul eden bir sorgu çağıran bir <xref:System.String> giriş parametresi ve döndürür bir `Contact` , e-posta adresi belirtilen dize ile başlar:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve kabul eden bir sorgu çağırır <xref:System.DateTime> ve <xref:System.Decimal> giriş parametreleri ve bir dizi siparişleri sipariş tarihi daha sonra 8 Mart 2003'ten olduğu ve son toplam döndürür olduğu değerinden $300.00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler ve kabul eden bir sorgu çağıran bir <xref:System.DateTime> giriş parametresi ve sipariş tarihi 8 Mart 2004'den sonraki olduğu siparişler bir dizi döndürür. Bu sorgu anonim türdeki bir dizisi olarak sipariş bilgilerini döndürür. Tür parametrelerinde belirtemezsiniz, anonim türler derleyici tarafından olayla <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi ve türü sorguda tanımlanır.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derler ve kullanıcı tanımlı yapısı giriş parametresi kabul edip siparişler bir dizi döndürür bir sorgu çağırır. Başlangıç tarihi ve bitiş tarihi toplam sorgu parametreleri son yapısını tanımlar ve sorgu Mart 3 ve 8 Mart 2003 arasında $700.00 büyük son toplam ile birlikte gelen siparişleri döndürür.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Sorgu parametreleri tanımlar yapısı:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Entity Framework birleştirme seçeneklerini ve derlenmiş sorguları](http://go.microsoft.com/fwlink/?LinkId=199591)
