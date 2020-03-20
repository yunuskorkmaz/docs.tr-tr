---
title: Sorgu Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: e372744eea3eed7fc3f7ee9c8bbdd711c95b586e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149979"
---
# <a name="query-execution"></a>Sorgu Yürütme
LINQ sorgusu bir kullanıcı tarafından oluşturulduktan sonra, bir komut ağacına dönüştürülür. Komut ağacı, Varlık Çerçevesi ile uyumlu bir sorgunun temsilidir. Komut ağacı daha sonra veri kaynağına karşı yürütülür. Sorgu yürütme sırasında, tüm sorgu ifadeleri (diğer bir deyişle, sorgunun tüm bileşenleri) sonuç maddeleştirmede kullanılan ifadeler de dahil olmak üzere değerlendirilir.  
  
 Sorgu ifadelerinin hangi noktada yürütüldürün farklı olabilir. LINQ sorguları her zaman sorgu değişkeni oluşturulduğunda değil, sorgu değişkeni üzerinde yinelendiğinde yürütülür. Buna *ertelenmiş yürütme*denir. Sorgu sonuçlarını önbelleğe almak için yararlı olan bir sorguyan sorgunun hemen yürütülmesi için de zorlayabilirsiniz. Bu daha sonra bu konuda açıklanmıştır.  
  
 LinQ to Ntities sorgusu yürütüldüğünde, sorgudaki bazı ifadeler sunucuda yürütülebilir ve bazı parçalar istemcide yerel olarak yürütülebilir. Sorgu sunucuda yürütülmeden önce bir ifadenin istemci tarafı değerlendirmesi gerçekleşir. İstemci üzerinde bir ifade değerlendirilirse, bu değerlendirmenin sonucu sorgudaki ifadenin yerine geçer ve sorgu daha sonra sunucuda yürütülür. Sorgular veri kaynağında yürütüldolduğundan, veri kaynağı yapılandırması istemcide belirtilen davranışı geçersiz kılar. Örneğin, null değer işleme ve sayısal kesinlik sunucu ayarlarına bağlıdır. Sunucuda sorgu yürütme sırasında atılan tüm özel durumlar doğrudan istemciye geçirilir.  

> [!TIP]
> Bir operatörün yürütme davranışını hızlı bir şekilde tanımlamanızı sağlayan tablo biçimindeki sorgu işleçlerinin kullanışlı bir özeti [için, Standart Sorgu Operatörlerinin Yürütme Şekline Göre Sınıflandırılması (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)bölümüne bakın.

## <a name="deferred-query-execution"></a>Ertelenmiş sorgu yürütme  
 Bir değer sırasını döndüren bir sorguda, sorgu değişkeninin kendisi hiçbir zaman sorgu sonuçlarını tutamaz ve yalnızca sorgu komutlarını depolar. Sorgunun yürütülmesi, sorgu değişkeni bir veya `foreach` `For Each` döngü içinde tekrarlanana kadar ertelenir. Bu ertelenmiş *yürütme*olarak bilinir; diğer bir tarihte, sorgu yürütmesi sorgu oluşturulduktan bir süre sonra gerçekleşir. Bu, bir sorguycığı istediğiniz kadar sık sık sık sık sık sık sık yürü/ Bu, örneğin, diğer uygulamalar tarafından güncelleştirilen bir veritabanınız olduğunda yararlıdır. Uygulamanızda, en son bilgileri almak ve her seferinde güncelleştirilmiş bilgileri döndürerek sorguyu tekrar tekrar yürütmek için bir sorgu oluşturabilirsiniz.  
  
 Ertelenmiş yürütme, birden çok sorgunun birleştirilmesini veya sorgunun genişletilmesini sağlar. Bir sorgu genişletildiğinde, yeni işlemleri içerecek şekilde değiştirilir ve nihai yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, ilk sorgu tüm ürünleri döndürür. İkinci sorgu, "L" `Where` boyutundaki tüm ürünleri döndürmek için kullanarak ilkini uzatır:  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Sorgu yürütüldükten sonra, birbirini izleyen tüm sorgular bellek içi LINQ işleçlerini kullanır. Bir `foreach` veya `For Each` deyim kullanarak veya LINQ dönüşüm işleçlerinden birini arayarak sorgu değişkenini yineleyerek hemen yürütmeye neden olur. Bu dönüştürme işleçleri <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A>şunlardır: , , <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Anında Sorgu Yürütme  
 Bir değer dizisi oluşturan sorguların ertelenmiş yürütmesinin aksine, singleton değerini döndüren sorgular hemen yürütülür. Singleton sorgularına bazı <xref:System.Linq.Enumerable.Average%2A>örnekler <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.First%2A>, <xref:System.Linq.Enumerable.Max%2A>, , ve . Sorgu singleton sonucunu hesaplamak için bir dizi üretmek gerekir, çünkü bu hemen yürütmek. Ayrıca derhal infazı da zorlayabilirsiniz. Bu, bir sorgunun sonuçlarını önbelleğe almak istediğinizde yararlıdır. Singleton değeri üretmeyen bir sorgunun hemen yürütülmesini zorlamak <xref:System.Linq.Enumerable.ToList%2A> için, <xref:System.Linq.Enumerable.ToDictionary%2A> bir sorgu <xref:System.Linq.Enumerable.ToArray%2A> veya sorgu değişkenindeki yöntemi, yöntemi veya yöntemi arayabilirsiniz. Aşağıdaki örnek, <xref:System.Linq.Enumerable.ToArray%2A> bir diziyi hemen bir diziye değerlendirmek için yöntemi kullanır.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Ayrıca, sorgu ifadesinden `foreach` hemen `For Each` sonra veya döngüyü koyarak <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A> yürütmeyi zorlayabilir, ancak tüm verileri tek bir toplama nesnesinde arayarak veya önbelleğe alarak.  
  
## <a name="store-execution"></a>Mağaza Yürütme  
 Genel olarak, LINQ'dan Varlıklara ifadeler sunucuda değerlendirilir ve ifadenin davranışının ortak dil çalışma zamanı (CLR) anlambilimini izlemesi beklenmemelidir, ancak veri kaynağının ifadeleri. Ancak, ifadeistemci üzerinde yürütüldüğünde olduğu gibi bunun istisnaları vardır. Bu, örneğin sunucu ve istemci farklı saat dilimlerindeyken beklenmeyen sonuçlara neden olabilir.  
  
 Sorgudaki bazı ifadeler istemcide yürütülebilir. Genel olarak, sorgu yürütmeçoğu sunucuda gerçekleşmesi bekleniyor. Sorgu öğelerine eşlenen sorgu öğelerine karşı yürütülen yöntemlerin yanı sıra, sorguda genellikle yerel olarak yürütülebilecek ifadeler vardır. Sorgu ifadesinin yerel yürütmesi, sorgu yürütmesinde veya sonuç yapısında kullanılabilecek bir değer verir.  
  
 Değerlerin, alt ifadelerin, kapatmalardan gelen alt sorguların ve nesnelerin sorgu sonuçlarına somutlaştırılması gibi istemcide her zaman belirli işlemler yürütülür. Bunun net etkisi, bu öğelerin (örneğin, parametre değerleri) yürütme sırasında güncelleştirilemememesidir. Anonim türler veri kaynağıüzerinde satır satır oluşturulabilir, ancak bunu yapmak için varsayılmamalıdır. Satır İçi gruplandırmalar da veri kaynağında oluşturulabilir, ancak bu her durumda varsayMamalıdır. Genel olarak, sunucuda ne inşa edilir hakkında herhangi bir varsayımda bulunmamak en iyisidir.  
  
 Bu bölümde, kodun istemci üzerinde yerel olarak yürütüldedildiği senaryolar açıklanmaktadır. Hangi ifade türlerinin yerel olarak yürütüldüğü hakkında daha fazla bilgi için, [LINQ' daki Ifadelerden Düzelme Cistirler ıÅ](expressions-in-linq-to-entities-queries.md)ığına bakın.  
  
### <a name="literals-and-parameters"></a>Literals ve Parametreler  
 Aşağıdaki örnekteki `orderID` değişken gibi yerel değişkenler istemci üzerinde değerlendirilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Yöntem parametreleri de istemci üzerinde değerlendirilir. `MethodParameterExample` Yönteme aktarılan `orderID` parametre, aşağıda bir örnektir.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Müşteri üzerinde Cast Literals  
 ClR `null` türünden döküm istemci üzerinde yürütülür:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Nullable <xref:System.Decimal>gibi bir türe döküm istemci üzerinde yürütülür:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Literals için Yapıcılar  
 Kavramsal model türlerine eşlenen yeni CLR türleri istemcide yürütülür:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 İstemci üzerinde yeni diziler de yürütülür.  
  
## <a name="store-exceptions"></a>Mağaza Özel Durumları  
 Sorgu yürütme sırasında karşılaşılan mağaza hataları istemciye aktarılır ve eşlenen veya işlenmez.  
  
## <a name="store-configuration"></a>Mağaza Yapılandırması  
 Sorgu mağazada yürütüldüğünde, mağaza yapılandırması tüm istemci davranışlarını geçersiz kılar ve tüm işlemler ve ifadeler için depo semantikleri ifade edilir. Bu, null karşılaştırmalar, GUID siparişi, kesinlik ve kesinlik içeren işlemlerin doğruluğu (kayan nokta türleri veya <xref:System.DateTime>), ve dize işlemleri gibi alanlarda CLR ve depo yürütme arasında davranış farkı neden olabilir. Sorgu sonuçlarını incelerken bunu göz önünde bulundurmak önemlidir.  
  
 Örneğin, CLR ve SQL Server arasındaki davranış farklılıkları şunlardır:  
  
- SQL Server GUID'leri CLR'den farklı şekilde sıralar.  
  
- Ayrıca, SQL Server'daki Ondalık yazıyla uğraşırken sonuç kesinliği açısından farklılıklar da olabilir. Bunun nedeni, SQL Server ondalık türünün sabit hassas gereksinimleridir. Örneğin, 0.0, 0.0 ve 1.0 değerlerinin <xref:System.Decimal> ortalaması 0.33333333333333333333333333333333333333333333333 istemcibellekte, ancak mağazada 0,333333333333 (SQL Server'ın ondalık türü için varsayılan kesinlik temel alınarak) olur.  
  
- Bazı dize karşılaştırma işlemleri de CLR daha SQL Server farklı işlenir. Dize karşılaştırma davranışı sunucudaki harmanlama ayarlarına bağlıdır.  
  
- Bir LINQ to Entity sorgusuna dahil edildiğinde işlev veya yöntem çağrıları, Entity Framework'deki kanonik işlevlere eşlenir ve bunlar daha sonra Transact-SQL'e çevrilmiş ve SQL Server veritabanında yürütülür. Bu eşlenen işlevlerin sergilediği davranış, taban sınıf kitaplıklarında uygulamafarklı olabilir durumlar vardır. Örneğin, parametre <xref:System.String.Contains%2A> <xref:System.String.StartsWith%2A>olarak <xref:System.String.EndsWith%2A> boş bir dize ile , `true` ve yöntemleri çağıran CLR yürütüldüğünde döndürülecektir, ancak SQL Server yürütüldüğünde dönecektir. `false` <xref:System.String.EndsWith%2A> YÖNTEM, SQL Server iki dizeyi yalnızca beyaz alanı izlemede farklılık gösterirse eşit olarak kabul ettiği için farklı sonuçlar döndürebilir, CLR ise bunları eşit olarak kabul eder. Bu aşağıdaki örnekle gösterilmiştir:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
