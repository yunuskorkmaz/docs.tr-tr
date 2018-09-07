---
title: LINQ to DataSet sorguları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: da9e5bd39cebce27dbaf89ac020c2bf8f154adcc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071706"
---
# <a name="queries-in-linq-to-dataset"></a>LINQ to DataSet sorguları
Bir sorgu, verileri bir veri kaynağından alır bir ifadedir. Sorgular genellikle ilişkisel veritabanları için SQL ve XML için XQuery gibi bir özel sorgu dilinde ifade edilir. Bu nedenle, geliştiriciler, her veri kaynağı veya veri biçimi, bunlar sorgu türü için yeni bir sorgu dili öğrenmek zorunda kalmışlardır. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] çeşitli veri kaynakları ve biçimler arasında verilerle çalışmak için daha basit ve tutarlı bir modeli sunar. İçinde bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu, çalıştığınız her zaman programlama nesneleri.  
  
 A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu işlemi üç eylemden oluşur: sorguyu veri kaynağından veya kaynaklarından elde etmek ve sorgu oluşturun.  
  
 Veri kaynakları uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirimi aracılığıyla sorgulanabilen [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Çağırma <xref:System.Data.DataTableExtensions.AsEnumerable%2A> üzerinde bir <xref:System.Data.DataTable> genel uygulayan bir nesne döndürür <xref:System.Collections.Generic.IEnumerable%601> veri kaynağı olarak hizmet veren arabirimi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgular.  
  
 Sorgu, veri kaynağından almak istediğiniz bilgi tam olarak belirtin. Bir sorgu, ayrıca nasıl bu bilgileri sıralanmış, gruplandırılmış ve döndürülmeden önce şeklinde belirtebilirsiniz. İçinde [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], sorguda bir değişkende depolanır. Değerleri bir dizisini döndürmek için sorguyu tasarlanmışsa, sorgu değişkeni sıralanabilir bir tür olmalıdır. Bu sorgu değişkeni hiç eylem almaması ve veri döndürmemesidir; yalnızca, sorgu bilgileri depolar. Bir sorguyu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.  
  
 Değerler döndüren bir sorgu, sorgu değişkeninin kendisi asla sorgu sonuçlarını tutar ve yalnızca sorgu komutlarını depolar. Sorgu yürütme sorgu değişkeni yinelenir kadar ertelenmiş bir `foreach` veya `For Each` döngü. Bu adlandırılır *ertelenmiş yürütme*; diğer bir deyişle, sorgu yürütme, sorgu oluşturulmuş sonra biraz zaman oluşur. Başka bir deyişle, bir sorgu istediğiniz sıklıkta yürütebilirsiniz. Örneğin, diğer uygulamalar tarafından güncelleştirilmiş bir veritabanı varsa, bu yararlıdır. Uygulamanızda döndüren güncelleştirilmiş bilgileri her zaman en son bilgileri almak ve sorguyu tekrar tekrar yürütmenin bir sorgu oluşturabilirsiniz.  
  
 Değerleri bir dizisini döndürmek, ertelenmiş sorguları aksine, bir tek değer döndüren sorgular hemen çalıştırılır. Bazı örnekler tek sorgu <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, ve <xref:System.Linq.Enumerable.First%2A>. Sorgu sonuçları tekil sonucu hesaplamak için gerekli olduğundan bu hemen yürütün. Ortalama işlevi çalışmak üzere giriş verilerini, örneğin, sorgu sonuçlarının ortalamasını bulmak için sorgu yürütülmelidir. Ayrıca <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> tek bir değer üretmiyor bir sorgu hemen yürütülmesini zorlamak için bir sorgu yöntemleri. Hemen yürütme zorlamak için bu teknikler, bir sorgunun sonuçlarını önbelleğe almak istediğiniz durumlarda yararlı olabilir. Ertelenmiş ve anlık sorgu yürütme hakkında daha fazla bilgi için bkz. [lınq'e Başlarken](https://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).  
  
## <a name="queries"></a>Sorgular  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları içinde iki farklı sözdizimini ifade: sorgu ifadesi söz dizimi ve metot tabanlı sorgu söz dizimi.  
  
### <a name="query-expression-syntax"></a>Sorgu ifadesi söz dizimi  
 Sorgu ifadeleri bir bildirim temelli bir sorgu söz dizimi var. Bu sözdizimi, C# veya Visual Basic'te bir SQL'e benzer bir biçimde sorgular yazmak bir geliştirici sağlar. Sorgu ifadesi söz dizimi kullanarak daha karmaşık filtreleme, sıralama ve gruplandırma işlemleri olabildiğince az kodla veri kaynaklarında gerçekleştirebilirsiniz. Daha fazla bilgi için [LINQ Sorgu ifadeleri](https://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) ve [temel sorgu işlemleri (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 Sorgu ifadesi söz dizimi C# 3.0 içinde yeni ve [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)]. Ancak, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR), sorgu ifade sözdizimi kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri CLR anlayan bir şey için çevrilmiş: yöntemi çağırır. Bu yöntemler olarak adlandırılır *standart sorgu işleçleri*. Bir geliştirici olarak, doğrudan sorgu söz dizimi yerine yöntem sözdizimi kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için [sorgu sözdizimi ve yöntem sözdizimi LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek `Product` tablo ve ürün adlarını görüntüler.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Metot tabanlı sorgu söz dizimi  
 Düzenleme için başka bir şekilde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgulardır yöntem temelli sorgular kullanarak. Metot tabanlı sorgu söz dizimi bir doğrudan yöntem çağrısına sırasıdır [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] işleci yöntemleri, lambda ifadeleri parametre olarak geçirerek. Daha fazla bilgi için [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Bu örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek `Product` ve ürün adlarını görüntüler.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Sorguları oluşturma  
 Sorgu değerleri bir dizisini döndürmek için tasarlanmıştır, bu konunun önceki kısımlarında belirtildiği gibi sorgu değişkeni yalnızca sorgu komutlarını depolar. Sorgu hemen yürütme neden olacak bir yöntem içermiyorsa, sorgunun gerçek yürütmesi içindeki sorgu değişkeni üzerinde yineleme kadar ertelenmiştir bir `foreach` veya `For Each` döngü. Ertelenmiş yürütme birleştirilecek birden çok sorgu veya sorgu genişletilmesi sağlar. Bir sorgu genişletildiğinde, yeni işlemler dahil etmek için değiştiren ve nihai yürütme değişiklikleri yansıtır. Aşağıdaki örnekte, ilk sorgu, tüm ürünleri döndürür. İkinci sorgu kullanarak ilk genişletir `Where` "L" boyuttaki tüm ürünleri döndürmek için:  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Sonra bir sorgu yürütüldüğü, ek sorgu yok oluşabilir ve izleyen tüm sorgular bellek içinde kullanacağınız [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] işleçleri. Sorgu yürütme içindeki sorgu değişkeni üzerinde yineleme yaptığınızda oluşacak bir `foreach` veya `For Each` deyimi veya biri için bir çağrı tarafından [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] hemen yürütme neden dönüştürme işleçleri. Bu işleçler şunlardır: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 Aşağıdaki örnekte, ilk sorgu fiyat listesi tarafından sıralanan tüm ürünleri döndürür. <xref:System.Linq.Enumerable.ToArray%2A> Yöntemi anlık sorgu yürütme zorlamak için kullanılır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [C#'de LINQ Kullanmaya Başlama](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Visual Basic'te lınq'e Başlarken](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
