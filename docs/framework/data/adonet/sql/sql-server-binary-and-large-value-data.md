---
title: SQL Server İkili ve Büyük Değerli Veriler
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791679"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="705bf-102">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="705bf-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="705bf-103">SQL Server,, `max` ve `nvarchar` `varchar` veri`varbinary` türlerinin depolama kapasitesini genişleten belirleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="705bf-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="705bf-104">`varchar(max)`, `nvarchar(max)` ve`varbinary(max)` topluca *büyük değerli veri türleri*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="705bf-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="705bf-105">En fazla 2 ^ 31-1 bayt veri depolamak için büyük değerli veri türlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705bf-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="705bf-106">SQL Server 2008, bir veri türü olmayan FıLESTREAM özniteliğini tanıtır, ancak bir sütunda tanımlanabilecek bir özniteliği yerine, büyük değerli verilerin veritabanı yerine dosya sisteminde depolanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="705bf-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="705bf-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="705bf-107">In This Section</span></span>  
 [<span data-ttu-id="705bf-108">ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="705bf-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="705bf-109">Büyük değerli veri türleriyle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="705bf-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="705bf-110">FILESTREAM Verileri</span><span class="sxs-lookup"><span data-stu-id="705bf-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="705bf-111">FıLESTREAM özniteliğiyle SQL Server 2008 ' de depolanan büyük değerli verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="705bf-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705bf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="705bf-112">See also</span></span>

- [<span data-ttu-id="705bf-113">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="705bf-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="705bf-114">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="705bf-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="705bf-115">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="705bf-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="705bf-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="705bf-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
