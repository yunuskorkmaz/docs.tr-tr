---
title: Saklı Yordamlarla Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: ebf5c61010a6f658d846ed435ea3a7d18d0d3832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934446"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="3e083-102">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3e083-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="3e083-103">Saklı yordamlar verileri giriş parametresi olarak kabul edebilir ve verileri çıkış parametreleri, sonuç kümeleri veya dönüş değerleri olarak döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3e083-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="3e083-104">Aşağıdaki örnek, ADO.NET 'in giriş parametrelerini, çıkış parametrelerini ve dönüş değerlerini nasıl göndereceğini ve alacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e083-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="3e083-105">Örnek, birincil anahtar sütununun SQL Server veritabanında bir kimlik sütunu olduğu tabloya yeni bir kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="3e083-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e083-106">Kullanarak veri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız <xref:System.Data.SqlClient.SqlDataAdapter>, saklı yordam tanımında set nocount kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3e083-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="3e083-107">Bu, etkilenen satırların sayısının sıfır olmasına neden olur ve bu da `DataAdapter` eşzamanlılık çakışması olarak yorumladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3e083-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="3e083-108">Bu olayda, bir <xref:System.Data.DBConcurrencyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e083-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e083-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e083-109">Example</span></span>  
 <span data-ttu-id="3e083-110">Örnek, **Northwind** **Categories** tablosuna yeni bir kategori eklemek için aşağıdaki saklı yordamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e083-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="3e083-111">Saklı yordam, **CategoryName** sütunundaki değeri bir giriş parametresi olarak alır ve Identity alanının yeni değerini almak için SCOPE_IDENTITY () işlevini kullanır, **CategoryID**ve bir output parametresinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e083-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="3e083-112">Return ifadesinde, eklenecek satırların sayısını@ROWCOUNT döndürmek için @ işlevi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e083-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="3e083-113">Aşağıdaki kod örneği, `InsertCategory` <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> için <xref:System.Data.SqlClient.SqlDataAdapter>kaynak olarak yukarıda gösterilen saklı yordamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e083-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="3e083-114">Çıkış parametresi, `Update` öğesinin <xref:System.Data.DataSet> yöntemiçağrıldığındakayıtveritabanınaeklendiktensonraöğesineyansıtılır<xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity`</span><span class="sxs-lookup"><span data-stu-id="3e083-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="3e083-115">Kod ayrıca dönüş değerini alır.</span><span class="sxs-lookup"><span data-stu-id="3e083-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e083-116">Kullanırken <xref:System.Data.OleDb.OleDbDataAdapter>, diğer parametrelerden önce bir <xref:System.Data.ParameterDirection> **returnValue** ile parametreleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e083-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3e083-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e083-117">See also</span></span>

- [<span data-ttu-id="3e083-118">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3e083-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="3e083-119">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="3e083-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="3e083-120">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="3e083-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="3e083-121">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3e083-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
