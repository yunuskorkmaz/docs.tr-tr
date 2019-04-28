---
title: Tablolar arası sorgular (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: e22df1148fab9148c1ca46f27e8603f55f71b34b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607780"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Tablolar arası sorgular (LINQ to DataSet)
Tek bir tabloyu sorgulamak ek tablolar arası sorgular içinde de gerçekleştirebilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Bu kullanılarak yapılır bir *birleştirme*. Bir veri kaynağı nesne kimliği başvurun ya da bir ürün gibi başka bir veri kaynağındaki ortak bir özniteliği paylaşan nesneleri ile ilişki join nedir Nesne yönelimli programlama, nesneleri arasındaki ilişkiler her bir nesnenin başka bir nesneye başvuran bir üyesine sahip olduğundan gitmek oldukça kolaydır. Dış veritabanı tablolarında ancak ilişkilerinde gezinme basit değildir. Veritabanı tabloları yerleşik ilişkileri içermez. Bu gibi durumlarda, her bir kaynaktan gelen öğelerle eşleme için birleştirme işlemi kullanılabilir. Örneğin, ürün bilgileri ve satış bilgilerini içeren iki tablo göz önünde bulundurulduğunda, satış bilgilerinin ve ürünleri için aynı satış siparişi eşleştirmek için bir birleştirme işlemi kullanabilirsiniz.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework sağlayan iki birleştirme işleçleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>. Bu işleçler gerçekleştirmek *benzer birleşimler*: diğer bir deyişle, iki veri eşleşen birleştirmeler kaynakları yalnızca kendi anahtarları eşit olduğunda. (Bunun aksine, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] destekler birleştirme işleçleri dışında `equals`, gibi `less than` işleci.)  
  
 İlişkisel veritabanı koşullarında <xref:System.Linq.Enumerable.Join%2A> iç birleşim gerçekleştirir. Bir iç birleştirme bir birleşim türünde de, yalnızca karşı veri kümesinde bir eşleşmeye sahip nesneler döndürülür.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> Operatörün doğrudan bir eşdeğer ilişkisel veritabanı bağlamında; İç birleşimler sol dış birleştirmeler ve bir üst uyguladıkları. İkinci koleksiyonda bağlantılı öğe yok bile bir sol dış birleşim ilk (soldaki) koleksiyonun her öğesine döndüren bir birleşim geçerlidir.  
  
 Birleşimler hakkında daha fazla bilgi için bkz. [birleştirme işlemleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geleneksel bir birleşim gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` Ağustos ay çevrimiçi siparişler edinme AdventureWorks örnek veritabanındaki tablolar.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Tek Tablolu Sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Birleştirme İşlemleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
