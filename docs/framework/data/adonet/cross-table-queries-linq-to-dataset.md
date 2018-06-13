---
title: Geçici Tablo Sorgu (LINQ-DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 17f9e683161fba0fe57279952acecd9e4399d0aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757196"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Geçici Tablo Sorgu (LINQ-DataSet)
Tek bir tablo sorgulama yanı sıra, geçici tablo sorguları da gerçekleştirebilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Bu kullanılarak yapılır bir *birleştirme*. Bir birleştirme nesnelerin bir veri kaynağı bir ürün gibi başka bir veri kaynağındaki ortak bir özniteliği paylaşan veya kimliği başvurun nesnelerle ilişkidir Nesne odaklı programlama içindeki nesneleri arasındaki ilişkiler her nesneyi başka bir nesneye başvuruda bulunan bir üye içerdiğinden gitmek görece kolaydır. Dış veritabanı tablolarında ancak ilişkilerinde gezinme kadar basit değildir. Veritabanı tabloları yerleşik ilişkileri içermez. Bu durumlarda, birleştirme işlemi her kaynak öğelerinden eşleştirmek için kullanılabilir. Örneğin, ürün bilgilerini ve satış bilgilerini içeren iki tablo verildiğinde, satış bilgilerini ve ürünleri aynı sipariş için eşleştirilecek bir birleştirme işlemi kullanabilirsiniz.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework sağlayan iki birleştirme işleçleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>. Bu işleçlere gerçekleştirmek *benzer birleşimler*: başka bir deyişle, iki veri eşleşen birleştirmeler kaynakları yalnızca kendi anahtarları eşit olduğunda. (Buna karşın [!INCLUDE[tsql](../../../../includes/tsql-md.md)] destekler birleştirme işleçleri dışında `equals`, gibi `less than` işleci.)  
  
 İlişkisel veritabanı terimleriyle <xref:System.Linq.Enumerable.Join%2A> bir iç birleştirme uygular. Bir iç birleştirme birleşim türünde içinde hangi ters veri kümesindeki bir eşleşme olan nesneler döndürülür.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> Operatörleri ilişkisel veritabanı bağlamında doğrudan bir eşdeğer sahiptir; İç birleşimler sol dış birleştirmeler ve bir alt kümesi uygulayan. Bu ikinci koleksiyonda ilişkili öğe olsa bile bir sol dış birleşim her öğesinin ilk (soldaki) koleksiyonu döndüren bir birleşim ' dir.  
  
 Birleşimler hakkında daha fazla bilgi için bkz: [birleştirme işlemleri](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geleneksel bir birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` Ağustos, month çevrimiçi olarak sipariş edinme AdventureWorks örnek veritabanı tablolarından.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Tek Tablolu Sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [Türü Belirtilmiş DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Birleştirme İşlemleri](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
