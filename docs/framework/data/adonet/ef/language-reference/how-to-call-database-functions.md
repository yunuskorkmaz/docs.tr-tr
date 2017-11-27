---
title: "Nasıl yapılır: çağrı veritabanı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dcc8c0bd232c6e88cbfc378d1c8df4ed3b11834e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-database-functions"></a>Nasıl yapılır: çağrı veritabanı işlevleri
<xref:System.Data.Objects.SqlClient.SqlFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için SQL Server işlevleri yöntemlerini içerir. Kullandığınızda <xref:System.Data.Objects.SqlClient.SqlFunctions> varlıklar sorguları, karşılık gelen veritabanı işlevleri LINQ yöntemlere veritabanında çalıştırılır.  
  
> [!NOTE]
>  Tek bir değer (Birleşik veritabanı işlevleri olarak da bilinir) bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve veritabanı işlevleri doğrudan çağrılabilir. Kurallı diğer işlevleri yalnızca bir LINQ to Entities sorgusunun bir parçası olarak çağrılabilir. Bir toplama işlevi doğrudan çağırmak için geçmesi gereken bir <xref:System.Data.Objects.ObjectQuery%601> işlevi. Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
> [!NOTE]
>  Yöntemlere <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfı için SQL Server işlevleri özeldir. Veritabanı işlevleri kullanıma benzer sınıflar diğer sağlayıcıları üzerinden kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Örnek bir LINQ to kullanan varlıklar sorgu yürütür <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> Soyadı tüm kişileri döndürülecek yöntemi "Si" ile başlar:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Örnek toplama çağırır <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> doğrudan yöntemi. Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işlevi geçirilir.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities sorgularında işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [LINQ to Entities sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
