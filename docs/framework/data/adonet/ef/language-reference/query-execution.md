---
title: Sorgu Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: f152146e7483c6b3c162fd81f20f359e6c82123a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614966"
---
# <a name="query-execution"></a>Sorgu Yürütme
Bir kullanıcı tarafından bir LINQ Sorgu oluşturulduktan sonra bu komut ağacına dönüştürülür. Bir komut ağacı, Entity Framework ile uyumlu bir sorgu gösterimidir. Komut ağacı veri kaynağına karşı yürütülür. Sorgu yürütme sırasında kullanılan söz konusu ifadelerden sonucu materialization dahil olmak üzere tüm sorgu ifadeleri (diğer bir deyişle, tüm bileşenleri sorgunun) değerlendirilir.  
  
 Hangi noktası sorgu ifadeleri çalıştırılan değişiklik gösterebilir. LINQ sorguları, sorgu değişkeni oluşturulmaz üzerinde sorgu değişkeni yinelendiğinde her zaman yürütülür. Bu adlandırılır *ertelenmiş yürütme*. Ayrıca, sorgu sonuçları önbelleğe almak için yararlı olan hemen yürütmek için bir sorgu zorlayabilirsiniz. Bu, bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
 Bir LINQ to Entities sorgusunda yürütüldüğünde, bazı sorgu ifadelerinde sunucu üzerinde yürütülen ve bazı bölümleri istemcide yerel olarak yürütüldüğü. Bir ifadenin değerlendirmesine istemci-tarafı sunucuda sorgu yürütülmeden önce gerçekleşir. İstemcide bir ifade değerlendirildiğinde, bu değerlendirme sonucu sorgu içindeki bir ifade değiştirilir ve sorgu sunucuda yürütülür. Veri kaynağında yürütülen sorgular için veri kaynağı yapılandırmasını istemci belirtilen davranışı geçersiz kılar. Örneğin, null değeri işleme ve sayısal duyarlık sunucusu ayarları bağlıdır. Sunucuda sorgu yürütme sırasında oluşturulan özel durumlar, doğrudan istemciye kadar geçirilir.  
 
> [!TIP]
> Sorgu işleçlerinin yürütme davranışını bir işlecin hızlıca belirlemenize olanak tanır, tablo biçiminde uygun bir özeti için bkz. [Sınıflandırma, standart sorgu işleçlerinin yürütme şekilde göre (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Ertelenen sorgu yürütme  
 Değerler döndüren bir sorgu, sorgu değişkeninin kendisi asla sorgu sonuçlarını tutar ve yalnızca sorgu komutlarını depolar. Sorgu yürütme sorgu değişkeni yinelenir kadar ertelenmiş bir `foreach` veya `For Each` döngü. Bu olarak bilinir *ertelenmiş yürütme*; diğer bir deyişle, sorgu yürütme, sorgu oluşturulmuş sonra biraz zaman oluşur. Başka bir deyişle, bir sorgu istediğiniz sıklıkla yürütebilirsiniz. Örneğin, diğer uygulamalar tarafından güncelleştirilmiş bir veritabanı varsa, bu yararlıdır. Uygulamanızda döndüren güncelleştirilmiş bilgileri her zaman en son bilgileri almak ve sorguyu tekrar tekrar yürütmenin bir sorgu oluşturabilirsiniz.  
  
 Ertelenmiş yürütme birleştirilecek birden çok sorgu veya sorgu genişletilmesi sağlar. Bir sorgu genişletildiğinde, yeni işlemler dahil etmek için değiştiren ve nihai yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, ilk sorgu, tüm ürünleri döndürür. İkinci sorgu kullanarak ilk genişletir `Where` "L" boyuttaki tüm ürünleri döndürmek için:  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Bir sorgu yürütüldükten sonra tüm ardışık sorgular bellek içi LINQ işleçleri kullanır. Kullanarak bir sorgu değişkeni üzerinde yineleme bir `foreach` veya `For Each` deyimini veya LINQ dönüştürme çağırarak işleçleri hemen yürütme neden olur. Bu dönüştürme işleçlerini şunları içerir: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Hemen bir sorgu yürütme  
 Değerler üreten sorgu aksine ertelenmiş yürütme hemen bir tekil değer döndüren sorgular yürütülür. Bazı örnekler tek sorgu <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A>, ve <xref:System.Linq.Enumerable.Max%2A>. Sorgu tekil sonucu hesaplamak için dizisi üretmesi gerekir çünkü bunlar hemen yürütün. Ayrıca, anında yürütmeyi zorlayabilirsiniz. Bir sorgunun sonuçlarını önbelleğe almak istediğiniz durumlarda kullanışlıdır. Tek bir değer üretmiyor bir sorgu hemen yürütülmesini zorlamak için çağırabilirsiniz <xref:System.Linq.Enumerable.ToList%2A> yöntemi <xref:System.Linq.Enumerable.ToDictionary%2A> yöntemi veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemi bir sorgu veya sorgu değişkeni. Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToArray%2A> hemen bir sıralı bir dizi içine değerlendirmek için bir yöntem.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Koyarak da yürütmeyi zorlayabilir `foreach` veya `For Each` döngü sorgu ifadesinin hemen sonra ancak çağırarak <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> tüm veriyi tek koleksiyon nesnesindeki önbelleğe alın.  
  
## <a name="store-execution"></a>Store yürütme  
 Genel olarak, sunucuda LINQ to Entities'de ifadeler değerlendirilir ve ifade davranışını ortak dil çalışma zamanı (CLR) semantiği, ancak bu veri kaynağının izlemek için beklendiği. İstisnaları vardır, ancak istemcide ifade ne zaman çalıştırılır gibi. Bu, örneğin, sunucu ve istemci, farklı saat dilimlerinde olduğunda beklenmeyen sonuçlara neden olabilir.  
  
 Bazı sorgu ifadelerinde istemcide yürütülmesi gerekir. Genel olarak, çoğu sorgu yürütme, sunucu üzerinde gerçekleşmesi beklenir. Sorgu öğelerinin eşlenmiş veri kaynağına karşı yürütülen yöntemler yanı sıra, genellikle yerel olarak yürütülebilecek sorgu ifadelerinde vardır. Sorgu ifadesinin yerel yürütme, sorgu yürütme ya da sonuç yapım kullanılabilmesi için bir değer verir.  
  
 Belirli işlemler her zaman yürütülür istemcide değerleri bağlama gibi ifadeler alt, alt sorguları kapanışlar ve sorgu sonuçları içine nesnelerin materialization. Bu net etkisiyle, yürütme sırasında bu öğeleri (örneğin, parametre değerlerini) güncelleştirilemiyor ' dir. Anonim türler veri kaynağında yapılandırılmış satır içi olabilir, ancak bunu yapmak için kabul yok edilmelidir. Satır içi gruplandırmaları veri kaynağında da oluşturulabilir ancak bu her örneğinde kabul edilmelidir değil. Genel olarak, sunucu üzerinde oluşturulan hakkında varsayımlar değil en iyisidir.  
  
 Bu bölümde, kodu yerel olarak istemcide yürütüldüğü senaryolar açıklanmaktadır. Hangi türde ifadeler yürütüldüğünde yerel olarak daha fazla bilgi için bkz. [ifadeleri LINQ to Entities sorgularında](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Değişmez değerleri ve parametreler  
 Yerel değişkenler gibi `orderID` aşağıdaki örnekte, değişken, istemcide değerlendirilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Yöntem parametreleri, istemcide ayrıca değerlendirilir. `orderID` Parametresi geçirildi `MethodParameterExample` yöntemi, bir örnek aşağıdadır.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>İstemcide değişmez değerler atama  
 Gelen atama `null` bir CLR türü istemcide çalıştırılır:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Gibi bir boş değer atanabilir bir tür için atama <xref:System.Decimal>, istemcide çalıştırılır:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Oluşturucular için değişmez değerleri  
 Kavramsal model türleri için eşlenmiş yeni CLR türleri, istemcide çalıştırılır:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Yeni diziler de istemcide çalıştırılır.  
  
## <a name="store-exceptions"></a>Store özel durumları  
 Sorgu yürütme işlemi sırasında karşılaşılan deposu hataları istemciye geçirilir ve değil eşlenen veya işlenen.  
  
## <a name="store-configuration"></a>Store yapılandırma  
 Sorgu deposu yürütüldüğünde, tüm istemci davranışlarını deposu yapılandırması geçersiz kılar ve depolama semantiği, tüm işlemleri ve ifadeleri cinsinden ifade edilir. Bu davranış birbirinden CLR neden ve null karşılaştırmalar, GUID sıralama, duyarlık ve hassas olmayan veri türleriyle ilgili işlemlerin doğruluğu gibi alanlardaki yürütme depolamak (kayan nokta türleri gibi veya <xref:System.DateTime>) ve dize işlemler. Bu sorgu sonuçları incelerken akılda tutulması önemlidir.  
  
 Örneğin, bazı CLR ve SQL Server arasındaki davranış farklılıkları şunlardır:  
  
- SQL Server CLR farklı GUID'leri sıralar.  
  
- Olabilir sonucu duyarlık farklılıkları SQL Server'daki ondalık türü ile ilgilenirken. SQL Server ondalık türdeki duyarlılığı sabit gereksinimleri nedeniyle budur. Örneğin, ortalama <xref:System.Decimal> değeri 0.0, 0.0 ve 1.0. istemci üzerindeki bellekte 0.3333333333333333333333333333 ancak 0.333333 (SQL Server'ın decimal türü için varsayılan duyarlık göre) depolama.  
  
- Bazı dize karşılaştırma işlemleri de farklı SQL Server CLR içinde işlenir. Harmanlama ayarları sunucuda dizesi karşılaştırma davranışı bağlıdır.  
  
- Bir LINQ to Entities sorgusunda dahil, daha sonra Transact-SQL çevrilir ve SQL Server veritabanında yürütülen varlık çerçevesi, kurallı işlevler eşlendiğine işlev veya metot çağrıları. Taban sınıfı kitaplıkları uygulamasında bu eşlenen işlevler göstermesi davranışı farklılık gösterebilir, durumlar vardır. Örneğin, çağırma <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, ve <xref:System.String.EndsWith%2A> yöntemleri ile parametre olarak boş bir dize döndürür `true` CLR'de yürütülür, ancak döndüreceği `false` SQL Server'da yürütüldüğünde. <xref:System.String.EndsWith%2A> SQL Server CLR eşit olmaması dikkate alır ancak yalnızca boşluk beyaz farklıysa eşit olacak şekilde iki dizeyi varsaydığı yöntemi farklı sonuçlar ayrıca döndürmeyebilir. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
