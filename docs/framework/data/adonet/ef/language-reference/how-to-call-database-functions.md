---
title: 'Nasıl yapılır: Veritabanı işlevleri çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 2b157f9ff1e87b54b965a3ed57865bf7963a7509
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742048"
---
# <a name="how-to-call-database-functions"></a>Nasıl yapılır: Veritabanı işlevleri çağırma
<xref:System.Data.Objects.SqlClient.SqlFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için SQL Server işlevleri yöntemlerini içerir. Kullanırken <xref:System.Data.Objects.SqlClient.SqlFunctions> yöntemleri LINQ to Entities sorgularında, karşılık gelen veritabanı işlevleri veritabanında yürütülür.  
  
> [!NOTE]
>  Bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve (toplam veritabanı işlevleri olarak da bilinir) tek bir değer döndürmesi veritabanı işlevleri doğrudan çağrılabilir. Diğer kurallı işlevler yalnızca bir LINQ to Entities sorgusunda bir parçası olarak çağrılabilir. Bir toplama işlevi doğrudan çağırmak için geçmelidir bir <xref:System.Data.Objects.ObjectQuery%601> işlevi. Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
> [!NOTE]
>  Yöntemlere <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfı SQL Server işleve özeldir. Veritabanı işlevler sunan benzer sınıflar diğer sağlayıcılar bulunabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Örnek bir LINQ to Entities sorgusunda, kullanır yürütür <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> Soyadı tüm kişileri döndürülecek yöntemi "B" ile başlar:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Örnek toplama çağırır <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> doğrudan yöntemi. Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunda parçası olmadan çağrılmasına izin veren işleve geçirilir.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
