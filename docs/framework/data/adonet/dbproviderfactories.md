---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 2376cf39228cb5e8208112333ba06bb80070de84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607002"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="009f6-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="009f6-102">DbProviderFactories</span></span>
<span data-ttu-id="009f6-103"><xref:System.Data.Common> Ad alanı oluşturmak için sınıflar sağlar <xref:System.Data.Common.DbProviderFactory> belirli veri kaynakları ile çalışmak için örnekleri.</span><span class="sxs-lookup"><span data-stu-id="009f6-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="009f6-104">Oluştururken bir <xref:System.Data.Common.DbProviderFactory> örneği ve veri sağlayıcısı hakkında bilgi geçirmek `DbProviderFactory` , verilen bilgilere göre tabanlı döndürmek için doğru türü kesin belirlenmiş bir bağlantı nesnesi belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="009f6-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="009f6-105">.NET Framework sürüm 4, veri sağlayıcıları gibi olarak başlayan <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, ve <xref:System.Data.OracleClient> machine.config dosyasının, ancak özel artık listelenen sağlayıcıları devam listelenmesi vardır.</span><span class="sxs-lookup"><span data-stu-id="009f6-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="009f6-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="009f6-106">In This Section</span></span>  
 [<span data-ttu-id="009f6-107">Fabrika Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="009f6-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="009f6-108">Fabrika tasarım deseni ve programlama arabirimi genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="009f6-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="009f6-109">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="009f6-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="009f6-110">Yüklü veri sağlayıcıları listeleme ve oluşturma yapmayı gösteren bir <xref:System.Data.Common.DbConnection> gelen bir `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="009f6-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="009f6-111">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="009f6-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="009f6-112">Nasıl oluşturulacağını gösterir bir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbDataReader>ve veri hatalarını kullanarak işleme <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="009f6-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="009f6-113">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="009f6-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="009f6-114">Nasıl kullanılacağını gösteren bir <xref:System.Data.Common.DbCommandBuilder> ile bir <xref:System.Data.Common.DbDataAdapter> almak ve verileri değiştirme.</span><span class="sxs-lookup"><span data-stu-id="009f6-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009f6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="009f6-115">See also</span></span>

- [<span data-ttu-id="009f6-116">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="009f6-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="009f6-117">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="009f6-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
