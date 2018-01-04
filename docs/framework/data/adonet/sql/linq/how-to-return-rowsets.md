---
title: "Nasıl yapılır: dönüş satır kümeleri"
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
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c5f88ce69239c0ca601344362dc420205291cb74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-rowsets"></a>Nasıl yapılır: dönüş satır kümeleri
Bu örnek veritabanından bir satır kümesi döndürür ve sonucu filtrelemek için bir giriş parametresi içerir.  
  
 Bir satır kümesi döndüren bir saklı yordamı çalıştırdığınızda, kullandığınız bir *sonuç* saklı yordamdan döndürür depolayan sınıf. Daha fazla bilgi için bkz: [çözümleme LINQ-SQL kaynak kodu](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşterilere satırlarını döndürür ve bu liste müşteri Şehir olarak "Londra" yalnızca bu satırları döndürmek için bir giriş parametresi kullanan bir saklı yordam temsil eder. Örnek bir numaralandırılabilir varsayar `CustomersByCityResult` sınıfı.  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
