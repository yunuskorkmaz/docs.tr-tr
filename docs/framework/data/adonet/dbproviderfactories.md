---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784095"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="f66a5-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="f66a5-102">DbProviderFactories</span></span>
<span data-ttu-id="f66a5-103">Ad <xref:System.Data.Common> alanı, belirli veri kaynaklarıyla <xref:System.Data.Common.DbProviderFactory> çalışacak örnekler oluşturmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f66a5-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="f66a5-104">Bir <xref:System.Data.Common.DbProviderFactory> örnek oluşturup veri sağlayıcısına `DbProviderFactory` ilişkin bilgileri geçirdiğinizde, sağlandığı bilgilere göre döndürülecek doğru ve kesin belirlenmiş bağlantı nesnesini belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f66a5-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="f66a5-105">.NET Framework sürüm 4 ' ten başlayarak, <xref:System.Data.Odbc>, ve <xref:System.Data.OracleClient> gibi <xref:System.Data.OleDb> <xref:System.Data.SqlClient>veri sağlayıcıları artık Machine. config dosyasında listelenmemiştir, ancak özel sağlayıcılar burada listelenmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="f66a5-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f66a5-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f66a5-106">In This Section</span></span>  
 [<span data-ttu-id="f66a5-107">Fabrika Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f66a5-107">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="f66a5-108">Fabrika tasarımı düzenine ve programlama arabirimine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f66a5-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="f66a5-109">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="f66a5-109">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="f66a5-110">Yüklü veri sağlayıcılarının nasıl ekleneceğini ve <xref:System.Data.Common.DbConnection> `DbProviderFactory`kaynağından bir oluşturma işlemlerinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f66a5-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="f66a5-111">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="f66a5-111">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="f66a5-112"><xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbException>Ve 'ninnasıloluşturulduğunuvekullanarakverihatalarınınnasılişleneceğinigösterir.<xref:System.Data.Common.DbDataReader></span><span class="sxs-lookup"><span data-stu-id="f66a5-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="f66a5-113">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f66a5-113">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="f66a5-114">Verileri almak ve değiştirmek <xref:System.Data.Common.DbCommandBuilder> <xref:System.Data.Common.DbDataAdapter> için ile birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f66a5-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f66a5-115">See also</span></span>

- [<span data-ttu-id="f66a5-116">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f66a5-116">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="f66a5-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f66a5-117">ADO.NET Overview</span></span>](ado-net-overview.md)
