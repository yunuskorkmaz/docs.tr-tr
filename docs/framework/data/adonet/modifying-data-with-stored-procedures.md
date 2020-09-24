---
title: Saklı Yordamlarla Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 65116a48533fd6ce86894c6a4522929285f8e1f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150758"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="23ed4-102">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="23ed4-102">Modifying Data with Stored Procedures</span></span>

<span data-ttu-id="23ed4-103">Saklı yordamlar verileri giriş parametresi olarak kabul edebilir ve verileri çıkış parametreleri, sonuç kümeleri veya dönüş değerleri olarak döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="23ed4-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="23ed4-104">Aşağıdaki örnek, ADO.NET 'in giriş parametrelerini, çıkış parametrelerini ve dönüş değerlerini nasıl göndereceğini ve alacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23ed4-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="23ed4-105">Örnek, birincil anahtar sütununun SQL Server veritabanında bir kimlik sütunu olduğu tabloya yeni bir kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="23ed4-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23ed4-106">Kullanarak veri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız <xref:System.Data.SqlClient.SqlDataAdapter> , saklı yordam TANıMıNDA SET NOCOUNT kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="23ed4-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="23ed4-107">Bu, etkilenen satırların sayısının sıfır olmasına neden olur ve bu da `DataAdapter` eşzamanlılık çakışması olarak yorumladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="23ed4-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="23ed4-108">Bu olayda, bir <xref:System.Data.DBConcurrencyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="23ed4-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23ed4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="23ed4-109">Example</span></span>  

 <span data-ttu-id="23ed4-110">Örnek, **Northwind** **Categories** tablosuna yeni bir kategori eklemek için aşağıdaki saklı yordamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="23ed4-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="23ed4-111">Saklı **yordam,** **CategoryName** sütunundaki değeri bir giriş parametresi olarak alır ve Identity alanının yeni değerini almak için SCOPE_IDENTITY () işlevini kullanır ve bunu bir çıkış parametresine döndürür.</span><span class="sxs-lookup"><span data-stu-id="23ed4-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="23ed4-112">RETURN ifadesinde, @ROWCOUNT eklenecek satırların sayısını döndürmek için @ işlevi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23ed4-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="23ed4-113">Aşağıdaki kod örneği, `InsertCategory` için kaynak olarak yukarıda gösterilen saklı yordamı kullanır <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="23ed4-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="23ed4-114">`@Identity`Çıkış parametresi, <xref:System.Data.DataSet> `Update` öğesinin yöntemi çağrıldığında kayıt veritabanına eklendikten sonra öğesine yansıtılır <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="23ed4-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="23ed4-115">Kod ayrıca dönüş değerini alır.</span><span class="sxs-lookup"><span data-stu-id="23ed4-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23ed4-116">Kullanırken <xref:System.Data.OleDb.OleDbDataAdapter> , <xref:System.Data.ParameterDirection> diğer parametrelerden önce bir **returnValue** ile parametreleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23ed4-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="23ed4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23ed4-117">See also</span></span>

- [<span data-ttu-id="23ed4-118">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="23ed4-118">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="23ed4-119">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="23ed4-119">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="23ed4-120">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="23ed4-120">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="23ed4-121">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="23ed4-121">ADO.NET Overview</span></span>](ado-net-overview.md)
