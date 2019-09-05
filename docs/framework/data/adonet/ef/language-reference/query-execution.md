---
title: Sorgu Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: fcf0d3eed95d36f7764ca048da62b589779d8d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249542"
---
# <a name="query-execution"></a>Sorgu Yürütme
Bir LINQ sorgusu bir kullanıcı tarafından oluşturulduktan sonra, bir komut ağacına dönüştürülür. Komut ağacı, Entity Framework uyumlu bir sorgunun gösterimidir. Komut ağacı daha sonra veri kaynağında yürütülür. Sorgu yürütme sırasında, sonuç materialization 'de kullanılan ifadeler de dahil olmak üzere tüm sorgu ifadeleri (yani, sorgunun tüm bileşenleri) değerlendirilir.  
  
 Hangi noktada sorgu ifadelerinin yürütüldüğü de farklılık gösterebilir. LINQ sorguları her zaman sorgu değişkeni, sorgu değişkeni oluşturulduğunda değil, üzerine yinelendiğinde yürütülür. Bu, *ertelenmiş yürütme*olarak adlandırılır. Ayrıca sorgu sonuçlarını önbelleğe almak için yararlı olan bir sorguyu hemen yürütmeye zorlayabilirsiniz. Bu konu başlığında daha sonra açıklanmaktadır.  
  
 Bir LINQ to Entities sorgusu yürütüldüğünde, sorgudaki bazı ifadeler sunucuda yürütülebilir ve bazı parçalar istemci üzerinde yerel olarak yürütülebilir olabilir. Sorgu sunucuda yürütülmeden önce bir ifadenin istemci tarafı değerlendirmesi gerçekleşir. İstemcide bir ifade değerlendirilirse, bu değerlendirmenin sonucu sorgudaki ifadeye göre değiştirilir ve sorgu daha sonra sunucuda yürütülür. Sorgular veri kaynağında yürütüldüğü için, veri kaynağı yapılandırması istemcide belirtilen davranışı geçersiz kılar. Örneğin, null değer işleme ve sayısal duyarlık sunucu ayarlarına bağlıdır. Sunucuda sorgu yürütme sırasında oluşturulan özel durumlar doğrudan istemciye geçirilir.  
 
> [!TIP]
> Bir işlecin yürütme davranışını hızlı bir şekilde belirlemenize olanak sağlayan tablo biçimindeki sorgu işleçlerinin uygun bir özeti için, bkz. [yürütme (C#) yöntemine göre standart sorgu işleçleri sınıflandırması](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Ertelenmiş sorgu yürütme  
 Bir dizi değer döndüren sorguda, sorgu değişkeni sorgu sonuçlarını hiçbir şekilde tutmayın ve yalnızca sorgu komutlarını depolar. Sorgunun yürütülmesi sorgu değişkeni bir `foreach` veya `For Each` döngüsünde yinelenene kadar ertelenir. Bu, *ertelenmiş yürütme*olarak bilinir; diğer bir deyişle sorgu yürütme, sorgu oluşturulduktan sonra bir süre oluşur. Bu, bir sorguyu istediğiniz sıklıkta yürütebilmeniz anlamına gelir. Bu, örneğin, diğer uygulamalar tarafından güncelleştirilmekte olan bir veritabanınız olduğunda faydalıdır. Uygulamanızda, en son bilgileri almak için bir sorgu oluşturabilir ve sorguyu sürekli olarak yürütebilir ve güncelleştirilmiş bilgileri her seferinde geri alabilirsiniz.  
  
 Ertelenmiş yürütme, birden çok sorgunun birleştirilmesi veya bir sorgunun genişletilmesini sağlar. Bir sorgu genişletildiğinde, yeni işlemleri içerecek şekilde değiştirilir ve nihai yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, ilk sorgu tüm ürünleri döndürür. İkinci sorgu, "L" boyutundaki tüm `Where` ürünleri döndürmek için kullanarak birincisini genişletir:  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Bir Sorgu yürütüldükten sonra, sonraki tüm sorgular bellek içi LINQ işleçlerini kullanır. `foreach` Or`For Each` ifadesini kullanarak veya LINQ dönüştürme işleçlerinden birini çağırarak sorgu değişkeninin üzerinde yineleme, hemen yürütmeye neden olur. Bu dönüştürme işleçleri şunları içerir <xref:System.Linq.Enumerable.ToList%2A>:, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Anlık sorgu yürütme  
 Değer dizisi üreten sorguların ertelenmiş yürütmesinin aksine, tek bir değer döndüren sorgular hemen yürütülür. <xref:System.Linq.Enumerable.Average%2A>Tekil sorguların bazı örnekleri <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.First%2A>,, ve <xref:System.Linq.Enumerable.Max%2A>' dir. Bu hemen yürütülür çünkü sorgu tekil sonucu hesaplamak için bir dizi üretmelidir. Ayrıca, hemen yürütmeye zorlayabilirsiniz. Bu, bir sorgunun sonuçlarını önbelleğe almak istediğinizde yararlıdır. Tek bir değer üretmeyen bir sorgunun hemen yürütülmesini zorlamak için, yöntemini, <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToDictionary%2A> yöntemini veya <xref:System.Linq.Enumerable.ToArray%2A> bir sorgu ya da sorgu değişkeninde yöntemi çağırabilirsiniz. Aşağıdaki örnek, bir diziyi <xref:System.Linq.Enumerable.ToArray%2A> bir diziye anında değerlendirmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Ayrıca, `foreach` veya `For Each` döngüsünü sorgu ifadesinden hemen sonra yerleştirerek, ancak çağırarak <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> tek bir koleksiyon nesnesindeki tüm verileri önbelleğe alarak yürütmeye zorlayabilirsiniz.  
  
## <a name="store-execution"></a>Mağaza yürütmesi  
 Genel olarak, LINQ to Entities ifadeler sunucuda değerlendirilir ve ifadenin davranışının ortak dil çalışma zamanı (CLR) semantiğinin izlenmesi beklenmemelidir, ancak veri kaynağı bu anlamlardır. Bununla birlikte, bu, örneğin, ifadenin istemcide yürütüldüğü durumlar gibi özel durumlar vardır. Bu, örneğin sunucu ve istemci farklı saat dilimlerinde olduğunda beklenmedik sonuçlara neden olabilir.  
  
 Sorgudaki bazı ifadeler istemcide çalıştırılabilir. Genel olarak, sunucuda çoğu sorgu yürütmenin gerçekleşmesi beklenir. Veri kaynağıyla eşlenen sorgu öğelerine karşı yürütülen yöntemlerin dışında, genellikle sorguda yerel olarak yürütülebilecek ifadeler vardır. Bir sorgu ifadesinin yerel yürütülmesi sorgu yürütme veya sonuç oluşturma içinde kullanılabilecek bir değer verir.  
  
 Belirli işlemler her zaman istemcide yürütülür, örneğin değerler, alt ifadeler, kapanışlardan alt sorgular ve nesnelerin sorgu sonuçlarına yürütülmesi gibi. Bunun net etkisi, bu öğelerin (örneğin, parametre değerleri) yürütme sırasında güncelleştirilemeyebilir. Anonim türler veri kaynağında satır içi olarak oluşturulabilir, ancak bunu yapması varsayılmamalıdır. Satır içi gruplandırmalar veri kaynağında da oluşturulabilir, ancak bu, her örnekte varsayılmamalıdır. Genel olarak, sunucuda oluşturulmuş olanlar hakkında varsayımlar yapmak en iyisidir.  
  
 Bu bölümde, kodun istemcide yerel olarak yürütüldüğü senaryolar açıklanmaktadır. Yerel olarak yürütülen tür ifadeler hakkında daha fazla bilgi için bkz. [LINQ to Entities sorgulardaki ifadeler](expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Sabit değerler ve parametreler  
 Aşağıdaki örnekteki `orderID` değişken gibi yerel değişkenler istemcisinde değerlendirilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Yöntem parametreleri de istemcide değerlendirilir. Aşağıdaki yönteme`MethodParameterExample` geçirilen parametrebirörnektir.`orderID`  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Istemcide sabit değerler atama  
 ' Dan `null` bir clr türüne atama, istemcide yürütülür:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Null yapılabilir <xref:System.Decimal>gibi bir türe atama, istemcide yürütülür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Sabit değerler için oluşturucular  
 Kavramsal model türlerine eşlenebilir yeni CLR türleri istemcisinde yürütülür:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Yeni diziler de istemcisinde yürütülür.  
  
## <a name="store-exceptions"></a>Özel durumları depola  
 Sorgu yürütme sırasında karşılaşılan tüm mağaza hataları istemciye geçirilir ve eşlenmez veya işlenmez.  
  
## <a name="store-configuration"></a>Mağaza yapılandırması  
 Sorgu mağazada yürütüldüğünde, mağaza yapılandırması tüm istemci davranışlarını geçersiz kılar ve depolama semantiği tüm işlemler ve ifadeler için ifade edilir. Bu durum, null karşılaştırmalar, GUID sıralaması, kesin olmayan veri türleri (kayan nokta türleri veya <xref:System.DateTime>) ve dize gibi alanlarda clr ve mağaza yürütmesi arasındaki davranışta farklılık oluşmasına neden olabilir operasyonları. Sorgu sonuçları incelenirken bunu göz önünde bulundurmanız önemlidir.  
  
 Örneğin, CLR ve SQL Server arasındaki davranıştaki bazı farklılıklar aşağıda verilmiştir:  
  
- GUID 'Leri CLR 'den farklı şekilde sıralar SQL Server.  
  
- Ayrıca, SQL Server ondalık türüyle ilgilenirken sonuç duyarlığına göre farklılık de olabilir. Bunun nedeni SQL Server Decimal türünün Sabit duyarlık gereksinimleridir. Örneğin, 0,0, 0,0 ve <xref:System.Decimal> 1,0 değerlerinin ortalaması istemcide 0.3333333333333333333333333333 'dir, ancak mağazada 0,333333 (SQL Server ondalık türü için varsayılan duyarlığa göre).  
  
- Bazı dize karşılaştırma işlemleri de SQL Server CLR 'de olandan farklı şekilde işlenir. Dize karşılaştırma davranışı, sunucudaki harmanlama ayarlarına bağlıdır.  
  
- İşlev veya yöntem çağrıları, bir LINQ to Entities sorgusuna dahil edildiğinde Entity Framework kurallı işlevlerle eşlenir ve bu da Transact-SQL ' e çevrilir ve SQL Server veritabanında yürütülür. Bu eşlenmiş işlevlerin sergileme davranışının temel sınıf kitaplıklarındaki uygulamadan farklı olması durumunda durumlar vardır. Örneğin, bir parametre olarak <xref:System.String.Contains%2A>boş <xref:System.String.StartsWith%2A>dize ile <xref:System.String.EndsWith%2A> ,, ve yöntemlerini çağırmak, clr 'de yürütüldüğünde döndürülür `true` , ancak SQL Server yürütüldüğünde döndürülür `false` . SQL Server iki dizeyi yalnızca sondaki boşluğa farklıysa, clr bunları eşit olmayan şekilde düşünürken, bu Yöntemfarklısonuçlardöndürebilir.<xref:System.String.EndsWith%2A> Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
