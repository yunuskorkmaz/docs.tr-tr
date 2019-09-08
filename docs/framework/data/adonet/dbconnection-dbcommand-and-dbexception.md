---
title: DbConnection, DbCommand ve DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 09526f111adeecb817ce4c4e587ca3713e0d8cde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785194"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="9616d-102">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="9616d-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="9616d-103"><xref:System.Data.Common.DbProviderFactory> Bir<xref:System.Data.Common.DbConnection>ve oluşturduktan sonra, veri kaynağından veri almak için komutlar ve veri okuyucularıyla çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9616d-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="9616d-104">Veri alma örneği</span><span class="sxs-lookup"><span data-stu-id="9616d-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="9616d-105">Bu örnek, bir `DbConnection` nesneyi bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="9616d-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="9616d-106">Bir <xref:System.Data.Common.DbCommand> SQL SELECT ifadesine <xref:System.Data.Common.DbCommand.CommandText%2A> ayarlayarak Kategoriler tablosundan verileri seçmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9616d-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="9616d-107">Kod, kategori tablosunun veri kaynağında bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9616d-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="9616d-108">Bağlantı açılır ve veriler bir <xref:System.Data.Common.DbDataReader>kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="9616d-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="9616d-109">Komut örneği yürütme</span><span class="sxs-lookup"><span data-stu-id="9616d-109">Executing a Command Example</span></span>  
 <span data-ttu-id="9616d-110">Bu örnek, bir `DbConnection` nesneyi bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="9616d-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="9616d-111">Geçerliyse bağlantı açılır <xref:System.Data.Common.DbCommand> ve oluşturulur ve yürütülür. `DbConnection`</span><span class="sxs-lookup"><span data-stu-id="9616d-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="9616d-112">, <xref:System.Data.Common.DbCommand.CommandText%2A> Northwind veritabanındaki Categories tablosuna bir INSERT uygulayan SQL INSERT ifadesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9616d-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="9616d-113">Kod, Northwind veritabanının veri kaynağında bulunduğunu ve INSERT ifadesinde kullanılan SQL sözdiziminin belirtilen sağlayıcı için geçerli olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9616d-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="9616d-114">Veri kaynağında oluşan hatalar <xref:System.Data.Common.DbException> kod bloğu tarafından işlenir ve diğer tüm özel durumlar <xref:System.Exception> bloğunda işlenir.</span><span class="sxs-lookup"><span data-stu-id="9616d-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="9616d-115">DbException ile veri hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="9616d-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="9616d-116"><xref:System.Data.Common.DbException> Sınıfı, bir veri kaynağı adına oluşturulan tüm özel durumlar için temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="9616d-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="9616d-117">Özel durum sınıfına başvuruda bulunmak zorunda kalmadan farklı sağlayıcılar tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunuzda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9616d-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="9616d-118">Aşağıdaki kod <xref:System.Data.Common.DbException> parçası, <xref:System.Exception.Source%2A> <xref:System.Exception.GetType%2A> ,<xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, ve<xref:System.Exception.Message%2A> özelliklerini kullanarak veri kaynağı tarafından döndürülen hata bilgilerini göstermek için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9616d-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="9616d-119">Çıktıda hata türü, sağlayıcı adını belirten kaynak, bir hata kodu ve hatayla ilişkili ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9616d-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9616d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9616d-120">See also</span></span>

- [<span data-ttu-id="9616d-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="9616d-121">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="9616d-122">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="9616d-122">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="9616d-123">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9616d-123">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="9616d-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9616d-124">ADO.NET Overview</span></span>](ado-net-overview.md)
