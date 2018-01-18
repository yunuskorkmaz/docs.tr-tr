---
title: "Sorgu Yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: db246037c388408e5722582049cf7a2b902caa18
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-execution"></a>Sorgu Yürütme
Bir kullanıcı tarafından bir LINQ Sorgu oluşturulduktan sonra bir komut ağacındaki dönüştürülür. Bir komut ağacındaki bir Entity Framework ile uyumlu bir sorgu gösterimidir. Komut ağacı veri kaynağında sonra yürütülür. Sorgu yürütme sırasında kullanılan ifadeleri sonuç materialization dahil olmak üzere tüm sorgu ifadeleri (diğer bir deyişle, tüm bileşenleri sorgunun) değerlendirilir.  
  
 Hangi noktası sorgu ifadeleri yürütülen adresindeki farklılık gösterebilir. Sorgu değişkeni oluşturulmaz üzerinden, sorgu değişkeni yinelendiğinde LINQ sorgularını her zaman yürütülür. Bu adlı *yürütme ertelenmiş*. Ayrıca, sorgu sonuçları önbelleğe alma işlemi için yararlı olan hemen yürütmek için bir sorgu zorlayabilirsiniz. Bu, bu konunun ilerleyen bölümlerinde açıklanan.  
  
 Bir LINQ to Entities sorgusunda yürütüldüğünde, bazı sorgu ifadelerinde sunucu üzerinde çalıştırılan ve bazı bölümleri istemci üzerinde yerel olarak yürütülen. Sunucuda sorgu yürütülmeden önce istemci tarafı bir ifadenin değerlendirmesine gerçekleşir. İstemcide bir ifadenin, sorgu ifadesinde için bu değerlendirme sonucu yerine ve sorgu sonra sunucu üzerinde çalıştırılabilir. Sorgu veri kaynağı üzerinde çalıştırıldığı için veri kaynağı yapılandırması istemci belirtilen davranışı geçersiz kılar. Örneğin, null değer işleme ve sayısal duyarlık sunucu ayarlarını bağlıdır. Sunucuda sorgu yürütme sırasında karşılaşılan özel durumlar doğrudan kadar istemci geçirilir.  
  
## <a name="deferred-query-execution"></a>Ertelenmiş sorgu yürütme  
 Değerleri dizisi döndüren bir sorgu, sorgu değişkeni hiçbir zaman sorgu sonuçlarını tutar ve yalnızca sorgu komutları depolar. Sorgunun içinde üzerinden sorgu değişkeni yinelendiğinde kadar ertelenmiş bir `foreach` veya `For Each` döngü. Bu olarak bilinir *yürütme ertelenmiş*; diğer bir deyişle, sorgu yürütme süre sorgu oluşturulan sonra oluşur. Bu sorgu için istediğiniz kadar sık yürütebilir anlamına gelir. Örneğin, diğer uygulamalar tarafından güncelleştirilmiş bir veritabanı varsa, bu yararlıdır. Uygulamanızda güncelleştirilmiş bilgileri her zaman döndürme en son bilgiler almak ve sorguyu tekrar tekrar yürütmek için bir sorgu oluşturabilirsiniz.  
  
 Ertelenmiş yürütme birleştirilecek birden çok sorgu veya bir sorgu genişletilmesi sağlar. Bir sorgu genişletildiğinde, yeni işlem içerecek şekilde değiştirilir ve son yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, tüm ürünleri ilk sorguyu döndürür. İkinci sorguyu kullanarak ilk genişletir `Where` "M" boyuttaki tüm ürünleri döndürmek için:  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Bir sorgu yürütüldükten sonra tüm art arda gelen sorguları bellek içi LINQ işleçleri kullanın. Kullanarak bir sorgu değişkeni yineleme yapma bir `foreach` veya `For Each` deyimi veya LINQ dönüştürme birini çağırarak işleçleri hemen yürütme neden olur. Bu dönüşüm işleçleri aşağıdakileri içerir: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Hemen sorgu yürütme  
 Değerleri dizisi üretir sorguları ertelenmiş yürütülmesi aksine, bir tek değer döndüren sorgular hemen çalıştırılır. Singleton sorguları bazı örnekleri şunlardır <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A>, ve <xref:System.Linq.Enumerable.Max%2A>. Sorgunun singleton sonucu hesaplamak için dizisi üretmesi gerekir çünkü bunlar hemen yürütün. Ayrıca, hemen yürütme zorlayabilirsiniz. Bir sorgunun sonuçlarını önbelleğe almak istediğiniz durumlarda kullanışlıdır. Bir tek değer üretmez bir sorgu hemen yürütülmesi zorlamak için çağırabilirsiniz <xref:System.Linq.Enumerable.ToList%2A> yöntemi, <xref:System.Linq.Enumerable.ToDictionary%2A> yöntemini veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemi bir sorgu veya sorgu değişkeni. Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToArray%2A> hemen bir dizi bir dizi içine değerlendirmek için bir yöntem.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Koyarak yürütme zorlayabilir `foreach` veya `For Each` döngü sorgu ifadesi hemen sonra ancak çağırarak <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> tek koleksiyon nesnesinde tüm verileri önbelleğe alma.  
  
## <a name="store-execution"></a>Depo yürütme  
 Genel olarak, LINQ to Entities içinde ifadeler sunucuda değerlendirilir ve ifade davranışını ortak dil çalışma zamanı (CLR) semantiği izleyin, ancak bu veri kaynağı için beklendiği. İstisnası vardır, ancak ifade istemci üzerinde ne zaman çalıştırıldığı gibi. Bu, sunucu ve istemci farklı bir saat dilimindeki olduğunda örneğin beklenmeyen sonuçlara neden olabilir.  
  
 Bazı sorgu ifadelerinde istemcide yürütülebilecek. Genel olarak, çoğu sorgu yürütme sunucu üzerinde gerçekleşmesi beklenir. Veri kaynağına eşlenen sorgusu öğeleri yürütülen yöntemleri yanı sıra, çoğunlukla yerel olarak çalıştırılabilir sorgu ifadelerinde vardır. Bir sorgu ifadesi yerel yürütülmesi sorgu yürütme veya sonuç yapım kullanılan bir değer verir.  
  
 Belirli işlemleri her zaman yürütülür istemcide bağlama değerleri gibi ifadeler sub, alt sorgular kapanışlar ve nesneleri materialization sorgu sonuçlarına. Bu öğeleri (örneğin, parametre değerlerini) yürütme sırasında güncelleştirilemez Bunun net etkisi olur. Anonim türler oluşturulan satır içi veri kaynağı üzerinde olabilir, ancak bunu yapmak için kabul değil. Satır içi gruplandırmaları veri kaynağında de oluşturulabilir, ancak bu her örneğinde kabul edilmelidir değil. Genel olarak, sunucu üzerinde oluşturulan hakkında varsayımlar yapmamak en iyisidir.  
  
 Bu bölümde kod yerel olarak istemcide yürütüldüğü senaryolar açıklanmaktadır. Hangi türde ifadeler yürütülme yerel olarak daha fazla bilgi için bkz: [LINQ to Entities sorgu ifadelerinde](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Değişmez değerler ve parametreleri  
 Yerel değişkenler gibi `orderID` değişkeni aşağıdaki örnekte, istemci üzerinde değerlendirilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Yöntem parametreleri de istemcide değerlendirilir. `orderID` Parametresi geçirildi `MethodParameterExample` yöntemi, bir örnek aşağıdadır.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>İstemcide değişmez değerler atama  
 Gelen atama `null` bir CLR türü istemcide çalıştırılır:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Null atanabilir gibi bir tür atama <xref:System.Decimal>, istemcide çalıştırılır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Değişmez değerler için oluşturucular  
 Kavramsal model türü eşlenebilir yeni CLR türleri, istemcide çalıştırılır:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Yeni diziler ayrıca istemcide çalıştırılır.  
  
## <a name="store-exceptions"></a>Depolama özel durumları  
 Sorgu yürütme sırasında karşılaşılan deposu hataları istemciye geçirilir ve değil eşlenen veya işlenmiş.  
  
## <a name="store-configuration"></a>Depolama yapılandırması  
 Sorgu deposu yürütüldüğünde, tüm istemci davranışlarını deposu yapılandırmayı geçersiz kılar ve deposu semantiği tüm işlemleri ve ifadeler için belirtilmiştir. Bu davranış CLR arasında fark neden ve null karşılaştırmaları, GUID sıralama, duyarlık ve kesin olmayan veri türleriyle ilgili işlemleri doğruluğunu gibi alanlarda yürütme depolamak (kayan nokta türleri gibi veya <xref:System.DateTime>) ve dize işlemler. Bu sorgu sonuçları incelerken göz önünde bulundurmanız önemlidir.  
  
 Örneğin, bazı CLR ve SQL Server arasındaki davranış farklılıkları şunlardır:  
  
-   SQL Server CLR farklı GUID'ler sıralar.  
  
-   Ayrıca olabilir sonuç duyarlık farklılıkları SQL Server'da Decimal türü ile ilgilenirken. SQL Server decimal türü Duyarlığı sabit gereksinimleri nedeniyle budur. Örneğin, ortalaması <xref:System.Decimal> 0.0, 0.0 ve 1.0 değerleri olan istemci üzerindeki bellekte 0.3333333333333333333333333333 ancak 0.333333 (SQL Server'ın decimal türü için varsayılan duyarlık bağlı olarak) deposunda.  
  
-   Bazı dize karşılaştırma işlemleri de CLR'den SQL Server'ın farklı bir şekilde işlenir. Dize karşılaştırma davranışı sunucu harmanlama ayarları bağlıdır.  
  
-   Bir LINQ to Entities sorgusunda dahil, ardından Transact-SQL çevrilen ve SQL Server veritabanına yürütülen Entity Framework, kurallı işlevlerde eşlenen işlev veya yöntem çağrısı. Bu eşlenen işlevler sergileyen davranışı temel sınıf kitaplıkları uygulamasında farklılık gösterebilir, durumlar vardır. Örneğin, arama <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, ve <xref:System.String.EndsWith%2A> yöntemleri kullanılarak bir parametre olarak boş bir dize döndürür `true` CLR yürütüldü, ancak döndürülecek `false` SQL Server'da çalıştırıldığında. <xref:System.String.EndsWith%2A> SQL Server CLR eşit olmadığı dikkate alır ancak yalnızca boşluk beyaz farklıysa eşit olacak şekilde iki dizeyi algıladığından yöntemi farklı sonuçlar ayrıca döndürmeyebilir. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
