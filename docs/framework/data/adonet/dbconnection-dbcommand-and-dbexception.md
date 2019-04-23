---
title: DbConnection, DbCommand ve DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 759b2f36f9d38cdac0cfe4ff8e451b38012493e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143838"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="9053c-102">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="9053c-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="9053c-103">Oluşturduktan sonra bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection>, sonra verileri veri kaynağından almak için komutlar ve veri okuyucu ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9053c-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="9053c-104">Örnek veri alma</span><span class="sxs-lookup"><span data-stu-id="9053c-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="9053c-105">Bu örnek alan bir `DbConnection` bağımsız değişken olarak nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9053c-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="9053c-106">A <xref:System.Data.Common.DbCommand> ayarlayarak kategoriler tablosundan verileri seçmek için oluşturulan <xref:System.Data.Common.DbCommand.CommandText%2A> SQL SELECT deyimi.</span><span class="sxs-lookup"><span data-stu-id="9053c-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="9053c-107">Kod kategorileri tablosu veri kaynağında bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9053c-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="9053c-108">Bağlantı açıldığında ve verileri kullanarak alınır bir <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="9053c-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="9053c-109">Bir komut örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9053c-109">Executing a Command Example</span></span>  
 <span data-ttu-id="9053c-110">Bu örnek alan bir `DbConnection` bağımsız değişken olarak nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9053c-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="9053c-111">Varsa `DbConnection` bağlantısı açıldığında, geçerli olduğundan ve <xref:System.Data.Common.DbCommand> oluşturulan ve yürütüldü.</span><span class="sxs-lookup"><span data-stu-id="9053c-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="9053c-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Kategorileri tabloya bir INSERT Northwind veritabanında gerçekleştiren SQL INSERT deyimi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9053c-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="9053c-113">Kod, Northwind veritabanına veri kaynağında var olduğundan ve INSERT deyiminde kullanılan SQL söz dizimi belirtilen sağlayıcı için geçerli olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9053c-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="9053c-114">Veri kaynağından oluşan hatalar olarak işlenmesini <xref:System.Data.Common.DbException> kod bloğu ve diğer tüm özel durumlar işlenir <xref:System.Exception> blok.</span><span class="sxs-lookup"><span data-stu-id="9053c-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="9053c-115">DbException ile veri hataları işleme</span><span class="sxs-lookup"><span data-stu-id="9053c-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="9053c-116"><xref:System.Data.Common.DbException> Adına bir veri kaynağı oluşturulan tüm özel durumlar için temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9053c-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="9053c-117">Bir özel durum sınıfı başvurmak zorunda kalmadan farklı sağlayıcıları tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunu bunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9053c-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="9053c-118">Aşağıdaki kod parçası nasıl kullanılacağını gösteren <xref:System.Data.Common.DbException> kullanarak veri kaynağına tarafından döndürülen hata bilgileri görüntülemek için <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, ve <xref:System.Exception.Message%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9053c-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="9053c-119">Çıkış, hata, sağlayıcı adı, bir hata kodu ve şu hata ile ilişkili ileti belirten bir kaynak türünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9053c-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9053c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9053c-120">See also</span></span>

- [<span data-ttu-id="9053c-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="9053c-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="9053c-122">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="9053c-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="9053c-123">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9053c-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="9053c-124">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9053c-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
