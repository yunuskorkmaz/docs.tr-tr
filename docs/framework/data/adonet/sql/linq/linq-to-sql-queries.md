---
title: LINQ to SQL Sorguları
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: c49644a866a6e245c6be1f9a8e8f95d003fd0191
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175232"
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL Sorguları

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SORGULARı LINQ içinde yaptığınız gibi aynı söz dizimini kullanarak tanımlarsınız. Tek fark, sorgularınızda başvurulan nesnelerin bir veritabanındaki öğelerle eşlendiğine ilişkin bir farktır. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir. Özellikle, uygulamanız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu yürütmeyi istemek için API 'yi kullanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sağlayıcı daha sonra SORGUYU SQL metnine dönüştürür ve ADO sağlayıcısına yürütmeyi devreder. ADO sağlayıcısı sorgu sonuçlarını bir olarak döndürür `DataReader` . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sağlayıcı, ADO sonuçlarını <xref:System.Linq.IQueryable> Kullanıcı nesneleri koleksiyonuna çevirir.  
  
> [!NOTE]
> .NET Framework yerleşik türlerinde çoğu Yöntem ve operatör SQL 'e doğrudan Çeviriler sağlar. LINQ tarafından çevrilemez olanlar, çalışma zamanı özel durumları oluşturur. Daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).  
  
 Aşağıdaki tabloda, LINQ ve sorgu öğeleri arasındaki benzerlikler ve farklar gösterilmektedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
|Öğe|LINQ sorgusu|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sorgulayamadı|  
|----------|----------------|----------------------------------------------------------------------|  
|Sorguyu tutan yerel değişkenin dönüş türü (diziler döndüren sorgular için)|Yorlar `IEnumerable`|Yorlar `IQueryable`|  
|Veri kaynağını belirtme|`From`(Visual Basic) veya `from` (C#) yan tümcesini kullanır|Aynı|  
|Filtreleme|`Where` / `where` Yan tümceyi kullanır|Aynı|  
|Gruplandırma|`Group…By` / `groupby` Yan tümceyi kullanır|Aynı|  
|Seçme (yansıtma)|`Select` / `select` Yan tümceyi kullanır|Aynı|  
|Ertelenmiş ve anında yürütme|Bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Aynı|  
|Birleştirmeleri uygulama|`Join` / `join` Yan tümceyi kullanır|`Join` / `join` Yan tümcesini kullanabilir, ancak daha etkin bir şekilde <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliğini kullanır. Daha fazla bilgi için bkz. [Ilişkiler genelinde sorgulama](querying-across-relationships.md).|  
|Uzaktan yerel yürütmeye karşı||Daha fazla bilgi için bkz. [uzak ve yerel yürütme](remote-vs-local-execution.md).|  
|Akış ve önbelleğe alınmış sorgulama karşılaştırması|Yerel bellek senaryosunda uygulanamaz||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Temel LINQ Sorgu İşlemleri](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ Sorgu İşlemlerinde Tür İlişkileri](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Sorgu Kavramları](query-concepts.md)
