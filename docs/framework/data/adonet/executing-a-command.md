---
title: Komut Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: d7d290c1c149f9eab2449c25e8d32f2568eb0277
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156465"
---
# <a name="executing-a-command"></a><span data-ttu-id="d2c59-102">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="d2c59-102">Executing a Command</span></span>

<span data-ttu-id="d2c59-103">.NET Framework eklenen her .NET Framework veri sağlayıcısının, öğesinden devralan kendi komut nesnesi vardır <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="d2c59-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="d2c59-104">OLE DB için .NET Framework Veri Sağlayıcısı bir nesne içerir, Veri Sağlayıcısı .NET Framework SQL Server bir nesne içerir, ODBC için .NET Framework veri sağlayıcısı bir nesne içerir <xref:System.Data.OleDb.OleDbCommand> <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.Odbc.OdbcCommand> ve Oracle için .NET Framework veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleCommand> nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="d2c59-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="d2c59-105">Bu nesnelerin her biri, aşağıdaki tabloda açıklandığı gibi komut türüne ve istenen dönüş değerine göre komutları yürütmek için yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="d2c59-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="d2c59-106">Komut</span><span class="sxs-lookup"><span data-stu-id="d2c59-106">Command</span></span>|<span data-ttu-id="d2c59-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d2c59-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="d2c59-108">Döndürür bir `DataReader` nesne.</span><span class="sxs-lookup"><span data-stu-id="d2c59-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="d2c59-109">Tek bir skaler değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2c59-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="d2c59-110">Herhangi bir satır döndürmeyen bir komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="d2c59-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="d2c59-111">Döndürür <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="d2c59-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d2c59-112">Yalnızca bir nesne için kullanılabilir `SqlCommand` .</span><span class="sxs-lookup"><span data-stu-id="d2c59-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="d2c59-113">Kesin belirlenmiş her komut nesnesi ayrıca <xref:System.Data.CommandType> , aşağıdaki tabloda açıklandığı gibi bir komut dizesinin nasıl yorumlandığını belirten bir sabit listesini destekler.</span><span class="sxs-lookup"><span data-stu-id="d2c59-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="d2c59-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="d2c59-114">CommandType</span></span>|<span data-ttu-id="d2c59-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2c59-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="d2c59-116">Veri kaynağında yürütülecek deyimleri tanımlayan bir SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="d2c59-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="d2c59-117">Saklı yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="d2c59-117">The name of the stored procedure.</span></span> <span data-ttu-id="d2c59-118">`Parameters`Giriş ve çıkış parametrelerine erişmek için bir komutun özelliğini kullanabilir ve hangi yöntemin çağrıldığı bağımsız olarak değerleri döndürebilirsiniz `Execute` .</span><span class="sxs-lookup"><span data-stu-id="d2c59-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="d2c59-119">Kullanırken `ExecuteReader` , dönüş değerleri ve çıkış parametreleri kapatılana kadar erişilebilir olmayacaktır `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="d2c59-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="d2c59-120">Bir tablonun adı.</span><span class="sxs-lookup"><span data-stu-id="d2c59-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d2c59-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2c59-121">Example</span></span>  

 <span data-ttu-id="d2c59-122">Aşağıdaki kod örneğinde, <xref:System.Data.SqlClient.SqlCommand> özelliklerini ayarlayarak bir saklı yordamı yürütmek için nasıl bir nesne oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2c59-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="d2c59-123">Bir <xref:System.Data.SqlClient.SqlParameter> nesnesi, saklı yordama giriş parametresini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2c59-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="d2c59-124">Komut yöntemi kullanılarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> ve ' dan alınan çıktı <xref:System.Data.SqlClient.SqlDataReader> konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2c59-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="d2c59-125">Sorun giderme komutları</span><span class="sxs-lookup"><span data-stu-id="d2c59-125">Troubleshooting Commands</span></span>  

 <span data-ttu-id="d2c59-126">SQL Server için .NET Framework Veri Sağlayıcısı, başarısız olan komut yürütmeleri ile ilgili aralıklı sorunları algılamanıza olanak tanımak için performans sayaçlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="d2c59-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="d2c59-127">Daha fazla bilgi için bkz. [performans sayaçları](performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="d2c59-127">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c59-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c59-128">See also</span></span>

- [<span data-ttu-id="d2c59-129">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2c59-129">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="d2c59-130">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="d2c59-130">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d2c59-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2c59-131">ADO.NET Overview</span></span>](ado-net-overview.md)
