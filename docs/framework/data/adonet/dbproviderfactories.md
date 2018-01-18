---
title: DbProviderFactories
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3e42682a466d778a83981cd6dd0d9daeecef8822
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dbproviderfactories"></a><span data-ttu-id="6b7de-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="6b7de-102">DbProviderFactories</span></span>
<span data-ttu-id="6b7de-103"><xref:System.Data.Common> Ad alanı oluşturmak için sınıflar sağlar <xref:System.Data.Common.DbProviderFactory> belirli veri kaynakları ile çalışacak biçimde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6b7de-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="6b7de-104">Oluştururken bir <xref:System.Data.Common.DbProviderFactory> örneği ve veri sağlayıcısı hakkında bilgi geçirmek `DbProviderFactory` onu sağlamış bilgileri tabanlı döndürmek için doğru kesin türü belirtilmiş bir bağlantı nesnesi belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b7de-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="6b7de-105">.NET Framework sürüm 4, veri sağlayıcıları gibi başlayan <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, ve <xref:System.Data.OracleClient> machine.config dosyasının, ancak özel artık listelenen sağlayıcıları devam listelenecek vardır.</span><span class="sxs-lookup"><span data-stu-id="6b7de-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b7de-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6b7de-106">In This Section</span></span>  
 [<span data-ttu-id="6b7de-107">Fabrika Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6b7de-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="6b7de-108">Fabrika tasarım deseni ve programlama arabirimi genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b7de-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="6b7de-109">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="6b7de-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="6b7de-110">Yüklü veri sağlayıcıları listesi ve oluşturmak nasıl gösteren bir <xref:System.Data.Common.DbConnection> gelen bir `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="6b7de-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="6b7de-111">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="6b7de-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="6b7de-112">Nasıl oluşturulduğunu gösteren bir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbDataReader>ve kullanarak veri hataların nasıl işleneceğini <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="6b7de-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="6b7de-113">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6b7de-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="6b7de-114">Nasıl kullanılacağını gösteren bir <xref:System.Data.Common.DbCommandBuilder> ile bir <xref:System.Data.Common.DbDataAdapter> almak ve veri değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="6b7de-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7de-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b7de-115">See Also</span></span>  
 [<span data-ttu-id="6b7de-116">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6b7de-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="6b7de-117">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6b7de-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
