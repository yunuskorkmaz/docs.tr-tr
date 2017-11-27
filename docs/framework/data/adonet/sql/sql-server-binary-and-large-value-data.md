---
title: "SQL Server ikili ve değeri büyük veri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9065f467cd353c17471db2c0d67001a188459819
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="f60ed-102">SQL Server ikili ve değeri büyük veri</span><span class="sxs-lookup"><span data-stu-id="f60ed-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="f60ed-103">SQL Server sağlar `max` depolama kapasitesini genişletir belirleyici `varchar`, `nvarchar`, ve `varbinary` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="f60ed-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="f60ed-104">`varchar(max)`, `nvarchar(max)`, ve `varbinary(max)` toplu olarak adlandırılır *büyük değer veri türleri*.</span><span class="sxs-lookup"><span data-stu-id="f60ed-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="f60ed-105">En fazla 2 depolamak için büyük değer veri türleri kullanabilirsiniz ^ 31-1 veri baytı sayısı.</span><span class="sxs-lookup"><span data-stu-id="f60ed-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="f60ed-106">SQL Server 2008 dosya sisteminde veritabanında depolanan büyük değer verilerinin vererek FILESTREAM öznitelik, bir veri türü değil, ancak bunun yerine bir sütuna, tanımlı bir öznitelik tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f60ed-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f60ed-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f60ed-107">In This Section</span></span>  
 [<span data-ttu-id="f60ed-108">ADO.NET büyük değer (Maks) verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="f60ed-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="f60ed-109">Büyük değer veri türleri ile çalışmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="f60ed-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="f60ed-110">FILESTREAM verileri</span><span class="sxs-lookup"><span data-stu-id="f60ed-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="f60ed-111">FILESTREAM özniteliği ile SQL Server 2008'de depolanan değeri büyük veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f60ed-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60ed-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f60ed-112">See Also</span></span>  
 [<span data-ttu-id="f60ed-113">SQL Server veri türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f60ed-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="f60ed-114">SQL Server veri işlemleri ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f60ed-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="f60ed-115">Alma ve ADO.NET veri değiştirme</span><span class="sxs-lookup"><span data-stu-id="f60ed-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="f60ed-116">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f60ed-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
