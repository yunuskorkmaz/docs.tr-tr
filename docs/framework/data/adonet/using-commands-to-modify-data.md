---
title: Verileri Değiştirmek için Komutları Kullanma
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: e2f61dbf74f28d026ae91a2bc8f5bb78530ffeac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177260"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="85338-102">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="85338-102">Using Commands to Modify Data</span></span>

<span data-ttu-id="85338-103">Bir .NET Framework veri sağlayıcısı kullanarak, bir veritabanı veya katalogda şema düzenlemesi gerçekleştirmek için saklı yordamları veya veri tanımlama dili deyimlerini (örneğin, CREATE TABLE ve ALTER COLUMN) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85338-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="85338-104">Bu komutlar bir sorgu olarak satır döndürmez, bu nedenle **komut** nesnesi onları işlemek Için bir **ExecuteNonQuery** sağlar.</span><span class="sxs-lookup"><span data-stu-id="85338-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="85338-105">Şemayı değiştirmek için **ExecuteNonQuery** kullanmanın yanı sıra, verileri değiştiren, ancak INSERT, Update ve DELETE gibi satırları döndürmeyen SQL deyimlerini işlemek için de bu yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85338-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="85338-106">Satırlar **ExecuteNonQuery** yöntemi tarafından döndürülmese de, giriş ve çıkış parametreleri ve dönüş değerleri, **komut** nesnesinin **Parameters** koleksiyonu aracılığıyla geçirilebilir ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="85338-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85338-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="85338-107">In This Section</span></span>  

 [<span data-ttu-id="85338-108">Bir Veri Kaynağındaki Verileri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="85338-108">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="85338-109">Bir veritabanındaki verileri değiştiren komutların veya saklı yordamların nasıl yürütüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="85338-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="85338-110">Katalog İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="85338-110">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="85338-111">Veritabanı şemasını değiştiren komutların nasıl yürütüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="85338-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85338-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85338-112">See also</span></span>

- [<span data-ttu-id="85338-113">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="85338-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="85338-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="85338-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="85338-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="85338-115">ADO.NET Overview</span></span>](ado-net-overview.md)
