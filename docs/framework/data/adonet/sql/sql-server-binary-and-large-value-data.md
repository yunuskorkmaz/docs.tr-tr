---
title: SQL Server ikili ve değeri büyük veri
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: c0202f6dc17d36fafb28206e17b71fc6d68d88c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363412"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="1a3ab-102">SQL Server ikili ve değeri büyük veri</span><span class="sxs-lookup"><span data-stu-id="1a3ab-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="1a3ab-103">SQL Server sağlar `max` depolama kapasitesini genişletir belirleyici `varchar`, `nvarchar`, ve `varbinary` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="1a3ab-104">`varchar(max)`, `nvarchar(max)`, ve `varbinary(max)` toplu olarak adlandırılır *büyük değer veri türleri*.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="1a3ab-105">En fazla 2 depolamak için büyük değer veri türleri kullanabilirsiniz ^ 31-1 veri baytı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="1a3ab-106">SQL Server 2008 dosya sisteminde veritabanında depolanan büyük değer verilerinin vererek FILESTREAM öznitelik, bir veri türü değil, ancak bunun yerine bir sütuna, tanımlı bir öznitelik tanıtır.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a3ab-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1a3ab-107">In This Section</span></span>  
 [<span data-ttu-id="1a3ab-108">ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1a3ab-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="1a3ab-109">Büyük değer veri türleri ile çalışmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="1a3ab-110">FILESTREAM Verileri</span><span class="sxs-lookup"><span data-stu-id="1a3ab-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="1a3ab-111">FILESTREAM özniteliği ile SQL Server 2008'de depolanan değeri büyük veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3ab-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a3ab-112">See Also</span></span>  
 [<span data-ttu-id="1a3ab-113">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1a3ab-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="1a3ab-114">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1a3ab-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="1a3ab-115">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1a3ab-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="1a3ab-116">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1a3ab-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
