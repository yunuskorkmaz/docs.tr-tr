---
description: 'Hakkında daha fazla bilgi edinin: SQL Server Ikili ve Large-Value verileri'
title: SQL Server İkili ve Büyük Değerli Veriler
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 8c7da5d504af0bc1beeea7e210a6fff4157fb090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767446"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="d4b0e-103">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="d4b0e-103">SQL Server Binary and Large-Value Data</span></span>

<span data-ttu-id="d4b0e-104">SQL Server,, `max` `varchar` `nvarchar` ve veri türlerinin depolama kapasitesini genişleten belirleyicisi sağlar `varbinary` .</span><span class="sxs-lookup"><span data-stu-id="d4b0e-104">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="d4b0e-105">`varchar(max)`, `nvarchar(max)` ve `varbinary(max)` topluca *büyük değerli veri türleri* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4b0e-105">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="d4b0e-106">En fazla 2 ^ 31-1 bayt veri depolamak için büyük değerli veri türlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4b0e-106">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="d4b0e-107">SQL Server 2008, bir veri türü olmayan FıLESTREAM özniteliğini tanıtır, ancak bir sütunda tanımlanabilecek bir özniteliği yerine, büyük değerli verilerin veritabanı yerine dosya sisteminde depolanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d4b0e-107">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4b0e-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d4b0e-108">In This Section</span></span>  

 [<span data-ttu-id="d4b0e-109">ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d4b0e-109">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="d4b0e-110">Büyük değerli veri türleriyle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4b0e-110">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="d4b0e-111">FILESTREAM Verileri</span><span class="sxs-lookup"><span data-stu-id="d4b0e-111">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="d4b0e-112">FıLESTREAM özniteliğiyle SQL Server 2008 ' de depolanan büyük değerli verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4b0e-112">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b0e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4b0e-113">See also</span></span>

- [<span data-ttu-id="d4b0e-114">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d4b0e-114">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="d4b0e-115">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d4b0e-115">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="d4b0e-116">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d4b0e-116">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="d4b0e-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4b0e-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
