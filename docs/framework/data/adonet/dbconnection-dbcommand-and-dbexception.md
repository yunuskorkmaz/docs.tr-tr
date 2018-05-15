---
title: DbConnection, DbCommand ve DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 419f152d45ec254efab9270f67ace6e46a6b96a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="d6c70-102">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="d6c70-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="d6c70-103">Oluşturduktan sonra bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection>, sonra veri kaynağından veri almak için komutlar ve veri okuyucu ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6c70-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="d6c70-104">Veri örneği alınıyor</span><span class="sxs-lookup"><span data-stu-id="d6c70-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="d6c70-105">Bu örnekte geçen bir `DbConnection` bağımsız değişken olarak nesne.</span><span class="sxs-lookup"><span data-stu-id="d6c70-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="d6c70-106">A <xref:System.Data.Common.DbCommand> ayarlayarak kategoriler tablosundan verileri seçmek için oluşturulan <xref:System.Data.Common.DbCommand.CommandText%2A> SQL SELECT deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6c70-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="d6c70-107">Kod, kategoriler tablosu veri kaynağında var olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="d6c70-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="d6c70-108">Bağlantı açıldığında ve veriler kullanılarak alınır bir <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d6c70-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="d6c70-109">Bir komut örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d6c70-109">Executing a Command Example</span></span>  
 <span data-ttu-id="d6c70-110">Bu örnekte geçen bir `DbConnection` bağımsız değişken olarak nesne.</span><span class="sxs-lookup"><span data-stu-id="d6c70-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="d6c70-111">Varsa `DbConnection` bağlantı açıldığında geçerli olduğundan ve bir <xref:System.Data.Common.DbCommand> oluşturulan ve yürütülemiyor.</span><span class="sxs-lookup"><span data-stu-id="d6c70-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="d6c70-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Northwind veritabanına kategorileri tabloya INSERT gerçekleştiren bir SQL INSERT deyimi için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d6c70-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="d6c70-113">Kod, Northwind veritabanı veri kaynağında var olduğunu ve INSERT deyiminde kullanılan SQL söz dizimi belirtilen sağlayıcı için geçerli olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="d6c70-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="d6c70-114">Veri kaynağında oluşan hatalar tarafından işlenmesini <xref:System.Data.Common.DbException> kod bloğu ve diğer tüm özel durumları işlenir <xref:System.Exception> bloğu.</span><span class="sxs-lookup"><span data-stu-id="d6c70-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="d6c70-115">DbException ile veri hataları işleme</span><span class="sxs-lookup"><span data-stu-id="d6c70-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="d6c70-116"><xref:System.Data.Common.DbException> Sınıfı, bir veri kaynağı adına oluşturulan tüm özel durumlar için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="d6c70-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="d6c70-117">Bir özel durum sınıfı başvurmak zorunda kalmadan farklı sağlayıcıları tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunu bunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6c70-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="d6c70-118">Aşağıdaki kod parçası nasıl kullanılacağı ortaya <xref:System.Data.Common.DbException> veri kaynağını kullanarak döndürülen hata bilgileri görüntülemek için <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, ve <xref:System.Exception.Message%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d6c70-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="d6c70-119">Çıkış hata, sağlayıcı adı, hata kodu ve hata ile ilişkili ileti gösteren kaynak türünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6c70-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6c70-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6c70-120">See Also</span></span>  
 [<span data-ttu-id="d6c70-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="d6c70-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="d6c70-122">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="d6c70-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="d6c70-123">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d6c70-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="d6c70-124">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d6c70-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
