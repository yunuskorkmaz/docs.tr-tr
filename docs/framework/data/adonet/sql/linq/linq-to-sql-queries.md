---
title: LINQ to SQL Sorguları
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 478138d26d6cdf656b2487c637a5eb13784126e9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634386"
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL Sorguları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları LINQ içinde yaptığınız gibi aynı söz dizimini kullanarak tanımlarsınız. Tek fark, sorgularınızda başvurulan nesnelerin bir veritabanındaki öğelerle eşlendiğine ilişkin bir farktır. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir. Daha açık olarak, uygulamanız sorgu yürütmeyi istemek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API 'sini kullanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlayıcı, sorguyu SQL Text 'e dönüştürür ve ADO sağlayıcısına yürütmeyi devreder. ADO sağlayıcısı sorgu sonuçlarını bir `DataReader`olarak döndürür. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlayıcı, ADO sonuçlarını Kullanıcı nesneleri <xref:System.Linq.IQueryable> koleksiyonuna çevirir.  
  
> [!NOTE]
> .NET Framework yerleşik türlerinde çoğu Yöntem ve operatör SQL 'e doğrudan Çeviriler sağlar. LINQ tarafından çevrilemez olanlar, çalışma zamanı özel durumları oluşturur. Daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).  
  
 Aşağıdaki tabloda, LINQ ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu öğeleri arasındaki benzerlikler ve farklar gösterilmektedir.  
  
|Öğe|LINQ sorgusu|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu|  
|----------|----------------|----------------------------------------------------------------------|  
|Sorguyu tutan yerel değişkenin dönüş türü (diziler döndüren sorgular için)|Genel `IEnumerable`|Genel `IQueryable`|  
|Veri kaynağını belirtme|`From` (Visual Basic) veya `from` (C#) yan tümcesini kullanır|Naklettiğiniz|  
|Filtreleme|`Where`/`where` yan tümcesini kullanır|Naklettiğiniz|  
|Gruplandırma|`Group…By`/`groupby` yan tümcesini kullanır|Naklettiğiniz|  
|Seçme (yansıtma)|`Select`/`select` yan tümcesini kullanır|Naklettiğiniz|  
|Ertelenmiş ve anında yürütme|Bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Naklettiğiniz|  
|Birleştirmeleri uygulama|`Join`/`join` yan tümcesini kullanır|`Join`/`join` yan tümcesini kullanabilir, ancak <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliğini daha etkin bir şekilde kullanır. Daha fazla bilgi için bkz. [Ilişkiler genelinde sorgulama](querying-across-relationships.md).|  
|Uzaktan yerel yürütmeye karşı||Daha fazla bilgi için bkz. [uzak ve yerel yürütme](remote-vs-local-execution.md).|  
|Akış ve önbelleğe alınmış sorgulama karşılaştırması|Yerel bellek senaryosunda uygulanamaz||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Temel LINQ Sorgu İşlemleri](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ Sorgu İşlemlerinde Tür İlişkileri](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Sorgu Kavramları](query-concepts.md)
