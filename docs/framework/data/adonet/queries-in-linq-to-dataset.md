---
title: LINQ to DataSet Sorguları
description: Veri kaynağını veya kaynaklarını alarak, sorgu oluşturarak ve sorguyu çalıştırarak LINQ to DataSet sorguları oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: 79026f66137b9e008de2ef7c3d33cb8bbd3b8ec3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177403"
---
# <a name="queries-in-linq-to-dataset"></a>LINQ to DataSet Sorguları

Sorgu, veri kaynağından veri alan bir ifadedir. Sorgular, genellikle ilişkisel veritabanları için SQL gibi özel bir sorgu dilinde ifade edilir ve XML için XQuery. Bu nedenle, geliştiricilerin sorgutıkları her bir veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmeleri gerekiyordu. Dil ile tümleşik sorgu (LINQ), çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik daha basit ve tutarlı bir model sunar. Bir LINQ sorgusunda, her zaman programlama nesneleriyle çalışırsınız.  
  
 Bir LINQ sorgu işlemi üç eylemden oluşur: veri kaynağını veya kaynaklarını alın, sorguyu oluşturun ve sorguyu yürütün.  
  
 Genel arabirimi uygulayan veri kaynakları, <xref:System.Collections.Generic.IEnumerable%601> LINQ aracılığıyla sorgulanabilir. <xref:System.Data.DataTableExtensions.AsEnumerable%2A>Bir üzerinde çağırmak <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> , LINQ to DataSet sorguları için veri kaynağı görevi gören genel arabirimi uygulayan bir nesne döndürür.  
  
 Sorguda, tam olarak veri kaynağından almak istediğiniz bilgileri belirtirsiniz. Bir sorgu, döndürülmeden önce bu bilgilerin nasıl sıralanacağını, gruplanacağını ve şekillendirilmiş olduğunu da belirtebilir. LINQ içinde, bir sorgu bir değişkende depolanır. Sorgu bir değer dizisi döndürecek şekilde tasarlanmışsa, sorgu değişkeninin kendisi sıralanabilir bir tür olması gerekir. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve veri döndürmez; yalnızca sorgu bilgilerini depolar. Bir sorgu oluşturduktan sonra, verileri almak için bu sorguyu yürütmeniz gerekir.  
  
 Bir dizi değer döndüren sorguda, sorgu değişkeni sorgu sonuçlarını hiçbir şekilde tutmayın ve yalnızca sorgu komutlarını depolar. Sorgunun yürütülmesi sorgu değişkeni bir veya döngüsünde yinelenene kadar ertelenir `foreach` `For Each` . Bu, *ertelenmiş yürütme*olarak adlandırılır; diğer bir deyişle sorgu yürütme, sorgu oluşturulduktan sonra bir süre oluşur. Bu, bir sorguyu istediğiniz sıklıkta yürütebileceğiniz anlamına gelir. Bu, örneğin, diğer uygulamalar tarafından güncelleştirilmekte olan bir veritabanınız olduğunda faydalıdır. Uygulamanızda, en son bilgileri almak için bir sorgu oluşturabilir ve sorguyu sürekli olarak yürütebilir ve güncelleştirilmiş bilgileri her seferinde geri alabilirsiniz.  
  
 Bir değer sırası döndüren ertelenmiş sorgulara karşılık olarak, tek bir değer döndüren sorgular hemen yürütülür. Tekil sorguların bazı örnekleri,, <xref:System.Linq.Enumerable.Count%2A> ve ' dir <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.First%2A> . Bu, tek sonuç hesaplamak için sorgu sonuçlarının gerekli olduğu için hemen yürütülür. Örneğin, sorgu sonuçlarının ortalamasını bulmak için sorgu yürütülmesi gerekir, böylece Average işlevinin birlikte çalışmak için giriş verileri vardır. <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A> Tek bir değer üretmeyen bir sorgunun hemen yürütülmesini zorlamak için bir sorgu üzerinde veya yöntemlerini de kullanabilirsiniz. Hemen yürütmeye zorlamak için bu teknikler, bir sorgunun sonuçlarını önbelleğe almak istediğinizde yararlı olabilir.
  
## <a name="queries"></a>Sorgular  

 LINQ to DataSet sorguları iki farklı Sözdizimde formüllenebilir: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi.  
  
### <a name="query-expression-syntax"></a>Sorgu Ifadesi söz dizimi  

 Sorgu ifadeleri bildirime dayalı bir sorgu sözdizimidir. Bu sözdizimi, bir geliştiricinin C# veya Visual Basic sorguları SQL 'e benzer bir biçimde yazmasını sağlar. Sorgu ifadesi söz dizimini kullanarak, çok az kodlu veri kaynakları üzerinde bile karmaşık filtreleme, sıralama ve gruplama işlemleri gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [LINQ sorgu ifadeleri](../../../csharp/linq/index.md#query-expression-overview) ve [temel sorgu işlemleri (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 .NET Framework ortak dil çalışma zamanı (CLR), sorgu ifadesi sözdiziminin kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri CLR 'nin anlayabileceği bir şeye çevrilir: Yöntem çağrıları. Bu yöntemlere *Standart sorgu işleçleri*denir. Bir geliştirici olarak, sorgu sözdizimini kullanmak yerine, bunları doğrudan yöntem sözdizimini kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Select%2A> tablosundan tüm satırları döndürmek `Product` ve ürün adlarını göstermek için kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Yöntem tabanlı sorgu söz dizimi  

 LINQ to DataSet sorguları formületmenin diğer yolu Yöntem tabanlı sorguları kullanmaktır. Yöntem tabanlı sorgu söz dizimi, LINQ operatörü yöntemlerine doğrudan yöntem çağrılarının bir dizidir ve Lambda ifadelerini parametreler olarak geçirerek. Daha fazla bilgi için bkz. [lambda ifadeleri](../../../csharp/language-reference/operators/lambda-expressions.md).  
  
 Bu örnek, <xref:System.Linq.Enumerable.Select%2A> içindeki tüm satırları döndürmek `Product` ve ürün adlarını göstermek için kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Sorgu oluşturma  

 Bu konuda daha önce bahsedildiği gibi, sorgu değişkeni yalnızca sorgu bir değer dizisi döndürecek şekilde tasarlandıysa sorgu komutlarını depolar. Sorgu, hemen yürütmeye neden olacak bir yöntem içermiyorsa, bir veya döngüsünde sorgu değişkeni üzerinde yineleme yapana kadar sorgunun gerçek yürütmesi ertelenir `foreach` `For Each` . Ertelenmiş yürütme, birden çok sorgunun birleştirilmesi veya bir sorgunun genişletilmesini sağlar. Bir sorgu genişletildiğinde, yeni işlemleri içerecek şekilde değiştirilir ve nihai yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, ilk sorgu tüm ürünleri döndürür. İkinci sorgu, `Where` "L" boyutundaki tüm ürünleri döndürmek için kullanarak birincisini genişletir:  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Bir Sorgu yürütüldükten sonra ek sorgu oluşturulamaz ve sonraki tüm sorgular bellek içi LINQ işleçlerini kullanacaktır. Sorgu, bir veya deyimindeki sorgu değişkeni üzerinde yineleme yaptığınızda `foreach` `For Each` ya da hemen yürütmeye neden olan LINQ dönüştürme işleçlerinden birine yapılan bir çağrı ile gerçekleşir. Bu işleçler şunları içerir: <xref:System.Linq.Enumerable.ToList%2A> , <xref:System.Linq.Enumerable.ToArray%2A> , <xref:System.Linq.Enumerable.ToLookup%2A> , ve <xref:System.Linq.Enumerable.ToDictionary%2A> .  
  
 Aşağıdaki örnekte, ilk sorgu liste fiyatına göre sıralanmış tüm ürünleri döndürür. <xref:System.Linq.Enumerable.ToArray%2A>Yöntemi hemen sorgu yürütmeye zorlamak için kullanılır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [C#'de LINQ'e Başlarken](../../../csharp/programming-guide/concepts/linq/index.md)
- [Visual Basic'te LINQ'e Başlarken](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
