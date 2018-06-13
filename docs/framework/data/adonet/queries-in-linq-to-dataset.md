---
title: LINQ-DataSet sorguları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: ef9334eec92ef06e5be07dae4391cdac43fed778
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362357"
---
# <a name="queries-in-linq-to-dataset"></a>LINQ-DataSet sorguları
Bir sorgu veri kaynağından verileri alan bir ifadedir. Sorguları genellikle ilişkisel veritabanları için SQL ve XML için XQuery gibi bir özel sorgu dili ifade edilir. Bu nedenle, geliştiricilerin her veri kaynağı veya bunlar sorgu veri biçimi türü için yeni bir sorgu dili öğrenin gerekirdi. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için daha basit ve tutarlı bir modeli sunar. İçinde bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu, çalışma her zaman nesneleri programlama ile.  
  
 A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu işlemi üç eylemlerini oluşur: veri kaynağı veya kaynakları edinme, sorguyu oluşturmak ve sorgu yürütün.  
  
 Veri kaynakları uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirim sorgulanan aracılığıyla [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Çağırma <xref:System.Data.DataTableExtensions.AsEnumerable%2A> üzerinde bir <xref:System.Data.DataTable> genel uygulayan bir nesne döndürür <xref:System.Collections.Generic.IEnumerable%601> için veri kaynağı görevi gören arabirimi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgular.  
  
 Sorgu, tam olarak veri kaynağından almak istediğiniz bilgileri belirtin. Bir sorgu de nasıl bu bilgileri sıralanmış, gruplandırılmış ve, döndürülmeden önce şeklinde belirtebilirsiniz. İçinde [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], sorgu bir değişkende depolanır. Sorgu değerleri dizisi döndürmek üzere tasarlanmış sorgu değişkeni numaralandırılabilir bir tür olması gerekir. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve hiçbir veri döndürür; yalnızca, sorgu bilgileri depolar. Bir sorgu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.  
  
 Değerleri dizisi döndüren bir sorgu, sorgu değişkeni hiçbir zaman sorgu sonuçlarını tutar ve yalnızca sorgu komutları depolar. Sorgunun içinde üzerinden sorgu değişkeni yinelendiğinde kadar ertelenmiş bir `foreach` veya `For Each` döngü. Bu adlı *yürütme ertelenmiş*; diğer bir deyişle, sorgu yürütme süre sorgu oluşturulan sonra oluşur. Bu sorgu, istediğiniz sıklıkta yürütebilir anlamına gelir. Örneğin, diğer uygulamalar tarafından güncelleştirilmiş bir veritabanı varsa, bu yararlıdır. Uygulamanızda güncelleştirilmiş bilgileri her zaman döndürme en son bilgiler almak ve sorguyu tekrar tekrar yürütmek için bir sorgu oluşturabilirsiniz.  
  
 Değerleri bir dizi döndürmesi ertelenmiş sorguları aksine, bir tek değer döndüren sorgular hemen çalıştırılır. Singleton sorguları bazı örnekleri şunlardır <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, ve <xref:System.Linq.Enumerable.First%2A>. Sorgu sonuçları singleton sonucu hesaplamak için gerekli olduğundan bu hemen yürütün. Ortalama işlevi çalışmak için giriş, örneğin, sorgu sonuçları ortalamasını bulmak için sorgu yürütülmelidir. Aynı zamanda <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> bir tek değer üretmez bir sorgu hemen yürütülmesi zorlamak için bir sorgu yöntemleri. Bir sorgunun sonuçlarını önbelleğe almak istediğiniz zaman hemen yürütme zorlamak için bu teknikler yararlı olabilir. Ertelenmiş ve hemen sorgu yürütme hakkında daha fazla bilgi için bkz: [LINQ ile çalışmaya başlama](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).  
  
## <a name="queries"></a>Sorgular  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu içinde iki farklı sözdizimi şeklide: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi.  
  
### <a name="query-expression-syntax"></a>Sorgu ifade sözdizimi  
 Sorgu ifadeleri bildirim temelli sorgu söz dizimi ' dir. Bu sözdiziminin sorguları SQL benzer bir biçimde C# veya Visual Basic yazmak bir geliştirici sağlar. Sorgu ifade sözdizimini kullanarak, daha karmaşık filtreleme, sıralama ve veri kaynaklarında çok az kod ile gruplandırma işlemleri gerçekleştirebilir. Daha fazla bilgi için bkz: [LINQ Sorgu ifadeleri](http://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) ve [temel sorgu işlemleri (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 C# 3. 0'sorgu ifade sözdizimi yenidir ve [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)]. Ancak, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR), sorgu ifade sözdizimi kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri bir şeye CLR anlamak çevrilebilir: yöntem çağrıları. Bu yöntemler denir *standart sorgu işleçleri*. Bir geliştirici olarak doğrudan sorgu sözdizimini kullanarak yerine yöntemi sözdizimini kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Standart sorgu işleçleri kullanma hakkında daha fazla bilgi için bkz: [NOT ın yapı: LINQ genel programlama kılavuzu](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049).  
  
 Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek `Product` tablo ve ürün adlarını görüntüler.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Yöntem temelli sorgu söz dizimi  
 Formüle başka bir şekilde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları kullanmaktır yöntem temelli sorgular. Yöntem temelli sorgu sözdizimini doğrudan yöntem çağrılarını dizisidir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] lambda ifadeleri parametre olarak geçirme işleci yöntemleri. Daha fazla bilgi için bkz: [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Bu örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek `Product` ve ürün adlarını görüntüler.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Sorgular oluşturma  
 Sorgu değerleri dizisi döndürmek üzere tasarlanmış, bu konuda daha önce belirtildiği gibi sorgu değişkeni yalnızca sorgu komutları depolar. Sorgu hemen yürütme neden olacak bir yöntem içermiyorsa, gerçek sorgunun yürütülmesi, sorgu değişkeninde üzerinden yineleme kadar ertelenir bir `foreach` veya `For Each` döngü. Ertelenmiş yürütme birleştirilecek birden çok sorgu veya bir sorgu genişletilmesi sağlar. Bir sorgu genişletildiğinde, yeni işlem içerecek şekilde değiştirilir ve son yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, tüm ürünleri ilk sorguyu döndürür. İkinci sorguyu kullanarak ilk genişletir `Where` "M" boyuttaki tüm ürünleri döndürmek için:  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Sonra bir sorgu yürütüldükten, hiçbir ek sorgular oluşur ve izleyen tüm sorgular bellek içi kullanacağı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] işleçler. Sorgu yürütme sorgu değişkeninde üzerinden yineleme yaparken oluşacak bir `foreach` veya `For Each` deyimi veya biri için bir çağrı tarafından [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] hemen yürütme neden dönüşüm işleçleri. Bu işleçler şunlardır: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 Aşağıdaki örnekte, ilk sorguyu fiyat listesi tarafından sıralanan tüm ürünleri döndürür. <xref:System.Linq.Enumerable.ToArray%2A> Yöntemi hemen sorgu yürütme zorlamak için kullanılır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [C#'de LINQ Kullanmaya Başlama](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Visual Basic'te Lınq'e Başlarken](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
