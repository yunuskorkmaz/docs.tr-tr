---
title: "Saklı yordamlar verilerle değiştirme"
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
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f8f0c37e5ac84d878f1d443d2bcc1e8ded099a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="86010-102">Saklı yordamlar verilerle değiştirme</span><span class="sxs-lookup"><span data-stu-id="86010-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="86010-103">Saklı yordamlar veri giriş parametreleri olarak kabul edebilir ve veri çıkış parametreleri, sonuç kümesi ya da dönüş değeri geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86010-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="86010-104">Aşağıdaki örnekte nasıl ADO.NET alıp gönderen giriş gösterilmektedir parametreleri, çıktı parametrelerini ve dönüş değerleri.</span><span class="sxs-lookup"><span data-stu-id="86010-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="86010-105">Örneğin, birincil anahtar sütunu bir kimlik sütunu bir SQL Server veritabanında olduğu bir tabloya yeni bir kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="86010-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86010-106">Düzenlemek veya kullanarak verileri silmek için SQL Server saklı yordamları kullanıyorsanız, bir <xref:System.Data.SqlClient.SqlDataAdapter>, saklı yordam tanımı'nda SET NOCOUNT ON kullanmadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="86010-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="86010-107">Bu sıfır olarak döndürülen etkilenen satırların sayısı neden olur, `DataAdapter` bir eşzamanlılık çakışması yorumlar.</span><span class="sxs-lookup"><span data-stu-id="86010-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="86010-108">Bu olay bir <xref:System.Data.DBConcurrencyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86010-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86010-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="86010-109">Example</span></span>  
 <span data-ttu-id="86010-110">Yeni bir kategori eklemek için aşağıdaki saklı yordamı örnek kullanır **Northwind** **kategorileri** tablo.</span><span class="sxs-lookup"><span data-stu-id="86010-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="86010-111">Saklı yordam değerini alır **CategoryName** sütunu bir giriş parametresi ve kullandığı SCOPE_IDENTITY() olarak işlev kimlik alanına yeni değerini almak için **adlı kullanıcı, Categoryıd'si**ve döndürün bir çıkış parametresi.</span><span class="sxs-lookup"><span data-stu-id="86010-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="86010-112">RETURN deyimi kullanan @@ROWCOUNT işlevi eklenen satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="86010-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="86010-113">Aşağıdaki kod örneğinde `InsertCategory` saklı yordamı için kaynak olarak yukarıda gösterilen <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> , <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="86010-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="86010-114">`@Identity` Çıktı parametresi olarak yansıtılabilir <xref:System.Data.DataSet> kaydı veritabanına eklendikten sonra `Update` yöntemi <xref:System.Data.SqlClient.SqlDataAdapter> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="86010-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="86010-115">Kod ayrıca dönüş değerini alır.</span><span class="sxs-lookup"><span data-stu-id="86010-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86010-116">Kullanırken <xref:System.Data.OleDb.OleDbDataAdapter>, parametrelerle belirtmelisiniz bir <xref:System.Data.ParameterDirection> , **ReturnValue** parametrelerden önce.</span><span class="sxs-lookup"><span data-stu-id="86010-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="86010-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86010-117">See Also</span></span>  
 [<span data-ttu-id="86010-118">Alma ve ADO.NET veri değiştirme</span><span class="sxs-lookup"><span data-stu-id="86010-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="86010-119">DataAdapters ve DataReader</span><span class="sxs-lookup"><span data-stu-id="86010-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="86010-120">Bir komutu yürütme</span><span class="sxs-lookup"><span data-stu-id="86010-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="86010-121">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="86010-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
