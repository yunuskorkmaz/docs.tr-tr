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
# <a name="how-to-return-rowsets"></a><span data-ttu-id="1a67d-102">Nasıl yapılır: dönüş satır kümeleri</span><span class="sxs-lookup"><span data-stu-id="1a67d-102">How to: Return Rowsets</span></span>
<span data-ttu-id="1a67d-103">Bu örnek veritabanından bir satır kümesi döndürür ve sonucu filtrelemek için bir giriş parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="1a67d-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="1a67d-104">Bir satır kümesi döndüren bir saklı yordamı çalıştırdığınızda, kullandığınız bir *sonuç* saklı yordamdan döndürür depolayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="1a67d-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="1a67d-105">Daha fazla bilgi için bkz: [çözümleme LINQ-SQL kaynak kodu](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="1a67d-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a67d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a67d-106">Example</span></span>  
 <span data-ttu-id="1a67d-107">Aşağıdaki örnek, müşterilere satırlarını döndürür ve bu liste müşteri Şehir olarak "Londra" yalnızca bu satırları döndürmek için bir giriş parametresi kullanan bir saklı yordam temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a67d-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="1a67d-108">Örnek bir numaralandırılabilir varsayar `CustomersByCityResult` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a67d-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a67d-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a67d-109">See Also</span></span>  
 [<span data-ttu-id="1a67d-110">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="1a67d-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="1a67d-111">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="1a67d-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
