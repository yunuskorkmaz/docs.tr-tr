---
description: 'Daha fazla bilgi edinin: DbProviderFactory'
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 735c78a846fc8df31a922acf90e587c6d96f4995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651268"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="92b8d-103">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="92b8d-103">DbProviderFactories</span></span>

<span data-ttu-id="92b8d-104"><xref:System.Data.Common>Ad alanı, <xref:System.Data.Common.DbProviderFactory> belirli veri kaynaklarıyla çalışacak örnekler oluşturmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b8d-104">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="92b8d-105">Bir <xref:System.Data.Common.DbProviderFactory> örnek oluşturup veri sağlayıcısına ilişkin bilgileri geçirdiğinizde, `DbProviderFactory` sağlandığı bilgilere göre döndürülecek doğru ve kesin belirlenmiş bağlantı nesnesini belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="92b8d-105">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="92b8d-106">.NET Framework sürüm 4 ' ten başlayarak,, ve gibi veri <xref:System.Data.Odbc> sağlayıcıları <xref:System.Data.OleDb> <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> artık machine.config dosyasında listelenmemiştir, ancak özel sağlayıcılar burada listelenmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="92b8d-106">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92b8d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="92b8d-107">In This Section</span></span>  

 [<span data-ttu-id="92b8d-108">Fabrika Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92b8d-108">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="92b8d-109">Fabrika tasarımı düzenine ve programlama arabirimine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b8d-109">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="92b8d-110">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="92b8d-110">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="92b8d-111">Yüklü veri sağlayıcılarının nasıl ekleneceğini ve kaynağından bir oluşturma işlemlerinin nasıl yapılacağını gösterir <xref:System.Data.Common.DbConnection> `DbProviderFactory` .</span><span class="sxs-lookup"><span data-stu-id="92b8d-111">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="92b8d-112">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="92b8d-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="92b8d-113">Ve ' nin nasıl oluşturulduğunu <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbDataReader> ve kullanarak veri hatalarının nasıl işleneceğini gösterir <xref:System.Data.Common.DbException> .</span><span class="sxs-lookup"><span data-stu-id="92b8d-113">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="92b8d-114">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="92b8d-114">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="92b8d-115"><xref:System.Data.Common.DbCommandBuilder> <xref:System.Data.Common.DbDataAdapter> Verileri almak ve değiştirmek için ile birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92b8d-115">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b8d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92b8d-116">See also</span></span>

- [<span data-ttu-id="92b8d-117">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="92b8d-117">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="92b8d-118">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92b8d-118">ADO.NET Overview</span></span>](ado-net-overview.md)
