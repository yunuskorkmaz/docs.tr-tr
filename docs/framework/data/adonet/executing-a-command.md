---
title: Komut Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: f749ea37e1655f006e4de26e7cb279b778fe4faf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795115"
---
# <a name="executing-a-command"></a><span data-ttu-id="10932-102">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="10932-102">Executing a Command</span></span>
<span data-ttu-id="10932-103">.NET Framework eklenen her .NET Framework veri sağlayıcısının, öğesinden <xref:System.Data.Common.DbCommand>devralan kendi komut nesnesi vardır.</span><span class="sxs-lookup"><span data-stu-id="10932-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="10932-104">OLE DB için .NET Framework veri sağlayıcısı bir <xref:System.Data.OleDb.OleDbCommand> nesne içerir, veri sağlayıcısı için .NET Framework SQL Server bir <xref:System.Data.SqlClient.SqlCommand> nesnesi içerir, ODBC için .NET Framework veri sağlayıcısı bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleCommand> nesne içerir.</span><span class="sxs-lookup"><span data-stu-id="10932-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="10932-105">Bu nesnelerin her biri, aşağıdaki tabloda açıklandığı gibi komut türüne ve istenen dönüş değerine göre komutları yürütmek için yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="10932-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="10932-106">Komut</span><span class="sxs-lookup"><span data-stu-id="10932-106">Command</span></span>|<span data-ttu-id="10932-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10932-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="10932-108">Döndürür bir `DataReader` nesne.</span><span class="sxs-lookup"><span data-stu-id="10932-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="10932-109">Tek bir skaler değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="10932-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="10932-110">Herhangi bir satır döndürmeyen bir komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="10932-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="10932-111"><xref:System.Xml.XmlReader>Döndürür.</span><span class="sxs-lookup"><span data-stu-id="10932-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="10932-112">Yalnızca bir `SqlCommand` nesne için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10932-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="10932-113">Kesin belirlenmiş her komut nesnesi Ayrıca, aşağıdaki <xref:System.Data.CommandType> tabloda açıklandığı gibi bir komut dizesinin nasıl yorumlandığını belirten bir sabit listesini destekler.</span><span class="sxs-lookup"><span data-stu-id="10932-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="10932-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="10932-114">CommandType</span></span>|<span data-ttu-id="10932-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10932-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="10932-116">Veri kaynağında yürütülecek deyimleri tanımlayan bir SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="10932-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="10932-117">Saklı yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="10932-117">The name of the stored procedure.</span></span> <span data-ttu-id="10932-118">Giriş ve çıkış parametrelerine `Parameters` erişmek için bir komutun özelliğini kullanabilir ve hangi `Execute` yöntemin çağrıldığı bağımsız olarak değerleri döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10932-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="10932-119">Kullanırken `ExecuteReader`, dönüş değerleri ve çıkış parametreleri kapatılana `DataReader` kadar erişilebilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="10932-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="10932-120">Bir tablonun adı.</span><span class="sxs-lookup"><span data-stu-id="10932-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10932-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="10932-121">Example</span></span>  
 <span data-ttu-id="10932-122">Aşağıdaki kod örneğinde, özelliklerini ayarlayarak bir saklı yordamı <xref:System.Data.SqlClient.SqlCommand> yürütmek için nasıl bir nesne oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10932-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="10932-123">Bir <xref:System.Data.SqlClient.SqlParameter> nesnesi, saklı yordama giriş parametresini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10932-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="10932-124">Komut <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi kullanılarak yürütülür ve ' <xref:System.Data.SqlClient.SqlDataReader> dan alınan çıktı konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="10932-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="10932-125">Sorun giderme komutları</span><span class="sxs-lookup"><span data-stu-id="10932-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="10932-126">SQL Server için .NET Framework Veri Sağlayıcısı, başarısız olan komut yürütmeleri ile ilgili aralıklı sorunları algılamanıza olanak tanımak için performans sayaçlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="10932-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="10932-127">Daha fazla bilgi için bkz. [performans sayaçları](performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="10932-127">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10932-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10932-128">See also</span></span>

- [<span data-ttu-id="10932-129">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="10932-129">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="10932-130">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="10932-130">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="10932-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="10932-131">ADO.NET Overview</span></span>](ado-net-overview.md)
