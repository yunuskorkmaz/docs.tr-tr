---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veritabanı Işlevleri çağırma'
title: 'Nasıl yapılır: Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: d5c5854d375546d1604b6e27e6f757f1e126f9b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724524"
---
# <a name="how-to-call-database-functions"></a>Nasıl yapılır: Veritabanı İşlevleri Çağırma

<xref:System.Data.Objects.SqlClient.SqlFunctions>Sınıfı, LINQ to Entities sorgularda kullanmak üzere SQL Server işlevleri sunan yöntemler içerir. <xref:System.Data.Objects.SqlClient.SqlFunctions>LINQ to Entities sorgularda Yöntemler kullandığınızda, karşılık gelen veritabanı işlevleri veritabanında yürütülür.  
  
> [!NOTE]
> Bir değer kümesi üzerinde hesaplama yapan ve tek bir değer döndüren (toplu veritabanı işlevleri olarak da bilinir) veritabanı işlevleri doğrudan çağrılabilir. Diğer kurallı işlevler, yalnızca bir LINQ to Entities sorgusunun parçası olarak çağrılabilir. Bir toplama işlevini doğrudan çağırmak için, işlevine bir öğesine geçirmeniz gerekir <xref:System.Data.Objects.ObjectQuery%601> . Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
> [!NOTE]
> <xref:System.Data.Objects.SqlClient.SqlFunctions>Sınıfındaki yöntemler SQL Server işlevlere özgüdür. Veritabanı işlevlerini kullanıma sunan benzer sınıflar, diğer sağlayıcılar aracılığıyla kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır. Örnek, <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> son adı "si" ile başlayan tüm kişileri döndürmek için yöntemini kullanan LINQ to Entities bir sorgu yürütür:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır. Örnek, <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> doğrudan toplama yöntemini çağırır. Öğesinin bir <xref:System.Data.Objects.ObjectQuery%601> LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işleve geçtiğini unutmayın.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgularında Çağırma İşlevleri](calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
