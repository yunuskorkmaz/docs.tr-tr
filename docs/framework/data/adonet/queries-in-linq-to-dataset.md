---
title: LINQ to DataSet Sorguları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: 5aaf33e5e2379ace4d32c59bd842889d0f9e32da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794542"
---
# <a name="queries-in-linq-to-dataset"></a>LINQ to DataSet Sorguları
Sorgu, veri kaynağından veri alan bir ifadedir. Sorgular, genellikle ilişkisel veritabanları için SQL gibi özel bir sorgu dilinde ifade edilir ve XML için XQuery. Bu nedenle, geliştiricilerin sorgutıkları her bir veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmeleri gerekiyordu. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]çeşitli veri kaynakları ve biçimler genelinde verilerle çalışmaya yönelik daha basit ve tutarlı bir model sunar. Bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorguda, her zaman programlama nesneleriyle çalışırsınız.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Sorgu işlemi üç eylemden oluşur: veri kaynağını veya kaynaklarını alın, sorguyu oluşturun ve sorguyu yürütün.  
  
 Genel arabirimi uygulayan veri kaynakları <xref:System.Collections.Generic.IEnumerable%601> , aracılığıyla [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]sorgulanabilir. <xref:System.Collections.Generic.IEnumerable%601> Bir <xref:System.Data.DataTableExtensions.AsEnumerable%2A> üzerindeçağırmak,LINQtoDataSetsorgularıiçinverikaynağıgörevigörengenelarabirimiuygulayanbirnesnedöndürür.<xref:System.Data.DataTable>  
  
 Sorguda, tam olarak veri kaynağından almak istediğiniz bilgileri belirtirsiniz. Bir sorgu, döndürülmeden önce bu bilgilerin nasıl sıralanacağını, gruplanacağını ve şekillendirilmiş olduğunu da belirtebilir. ' [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]De, bir sorgu bir değişkende depolanır. Sorgu bir değer dizisi döndürecek şekilde tasarlanmışsa, sorgu değişkeninin kendisi sıralanabilir bir tür olması gerekir. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve veri döndürmez; yalnızca sorgu bilgilerini depolar. Bir sorgu oluşturduktan sonra, verileri almak için bu sorguyu yürütmeniz gerekir.  
  
 Bir dizi değer döndüren sorguda, sorgu değişkeni sorgu sonuçlarını hiçbir şekilde tutmayın ve yalnızca sorgu komutlarını depolar. Sorgunun yürütülmesi sorgu değişkeni bir `foreach` veya `For Each` döngüsünde yinelenene kadar ertelenir. Bu, *ertelenmiş yürütme*olarak adlandırılır; diğer bir deyişle sorgu yürütme, sorgu oluşturulduktan sonra bir süre oluşur. Bu, bir sorguyu istediğiniz sıklıkta yürütebileceğiniz anlamına gelir. Bu, örneğin, diğer uygulamalar tarafından güncelleştirilmekte olan bir veritabanınız olduğunda faydalıdır. Uygulamanızda, en son bilgileri almak için bir sorgu oluşturabilir ve sorguyu sürekli olarak yürütebilir ve güncelleştirilmiş bilgileri her seferinde geri alabilirsiniz.  
  
 Bir değer sırası döndüren ertelenmiş sorgulara karşılık olarak, tek bir değer döndüren sorgular hemen yürütülür. <xref:System.Linq.Enumerable.Count%2A>Tekil sorguların bazı örnekleri <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Average%2A>,, ve <xref:System.Linq.Enumerable.First%2A>' dir. Bu, tek sonuç hesaplamak için sorgu sonuçlarının gerekli olduğu için hemen yürütülür. Örneğin, sorgu sonuçlarının ortalamasını bulmak için sorgu yürütülmesi gerekir, böylece Average işlevinin birlikte çalışmak için giriş verileri vardır. Tek bir değer üretmeyen <xref:System.Linq.Enumerable.ToList%2A> bir <xref:System.Linq.Enumerable.ToArray%2A> sorgunun hemen yürütülmesini zorlamak için bir sorgu üzerinde veya yöntemlerini de kullanabilirsiniz. Hemen yürütmeye zorlamak için bu teknikler, bir sorgunun sonuçlarını önbelleğe almak istediğinizde yararlı olabilir.
  
## <a name="queries"></a>Sorgular  
 LINQ to DataSet sorguları iki farklı Sözdizimde formüllenebilir: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi.  
  
### <a name="query-expression-syntax"></a>Sorgu Ifadesi söz dizimi  
 Sorgu ifadeleri bildirime dayalı bir sorgu sözdizimidir. Bu sözdizimi, C# BIR geliştiricinin SQL 'e benzer bir biçimde veya Visual Basic sorguları yazmasına olanak sağlar. Sorgu ifadesi söz dizimini kullanarak, çok az kodlu veri kaynakları üzerinde bile karmaşık filtreleme, sıralama ve gruplama işlemleri gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [LINQ sorgu ifadeleri](../../../csharp/linq/index.md#query-expression-overview) ve [temel sorgu işlemleri (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 .NET Framework ortak dil çalışma zamanı (CLR), sorgu ifadesi sözdiziminin kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri CLR 'nin anlayabileceği bir şeye çevrilir: Yöntem çağrıları. Bu yöntemlere *Standart sorgu işleçleri*denir. Bir geliştirici olarak, sorgu sözdizimini kullanmak yerine, bunları doğrudan yöntem sözdizimini kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Aşağıdaki örnek, `Product` tablosundan <xref:System.Linq.Enumerable.Select%2A> tüm satırları döndürmek ve ürün adlarını göstermek için kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Yöntem tabanlı sorgu söz dizimi  
 LINQ to DataSet sorguları formületmenin diğer yolu Yöntem tabanlı sorguları kullanmaktır. Yöntem tabanlı sorgu söz dizimi, işleç yöntemlerine yönelik [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] doğrudan yöntem çağrılarının bir dizidir ve lambda ifadeleri parametre olarak geçirerek. Daha fazla bilgi için bkz. [lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Bu örnek, <xref:System.Linq.Enumerable.Select%2A> içindeki `Product` tüm satırları döndürmek ve ürün adlarını göstermek için kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Sorgu oluşturma  
 Bu konuda daha önce bahsedildiği gibi, sorgu değişkeni yalnızca sorgu bir değer dizisi döndürecek şekilde tasarlandıysa sorgu komutlarını depolar. Sorgu, hemen yürütmeye neden olacak bir yöntem içermiyorsa, bir `foreach` veya `For Each` döngüsünde sorgu değişkeni üzerinde yineleme yapana kadar sorgunun gerçek yürütmesi ertelenir. Ertelenmiş yürütme, birden çok sorgunun birleştirilmesi veya bir sorgunun genişletilmesini sağlar. Bir sorgu genişletildiğinde, yeni işlemleri içerecek şekilde değiştirilir ve nihai yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, ilk sorgu tüm ürünleri döndürür. İkinci sorgu, "L" boyutundaki tüm `Where` ürünleri döndürmek için kullanarak birincisini genişletir:  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Bir Sorgu yürütüldükten sonra ek sorgu oluşturulamaz ve sonraki tüm sorgular bellek [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] içi işleçleri kullanacaktır. Sorgu, bir `foreach` veya `For Each` deyimindeki sorgu değişkeni üzerinde yineleme yaptığınızda veya anında yürütmeye neden olan [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dönüştürme işleçlerinden birine yapılan bir çağrı ile gerçekleşir. Bu işleçler şunları içerir <xref:System.Linq.Enumerable.ToList%2A>:, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 Aşağıdaki örnekte, ilk sorgu liste fiyatına göre sıralanmış tüm ürünleri döndürür. <xref:System.Linq.Enumerable.ToArray%2A> Yöntemi hemen sorgu yürütmeye zorlamak için kullanılır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [C#'de LINQ Kullanmaya Başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Visual Basic LINQ ile çalışmaya başlama](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
