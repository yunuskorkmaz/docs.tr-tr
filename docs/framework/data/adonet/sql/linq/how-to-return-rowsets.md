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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c2a11ae83be1c7f75c5bc440c5f8162877106b07
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
