---
title: Verileri Değiştirmek için Komutları Kullanma
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875959"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="72d4d-102">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="72d4d-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="72d4d-103">.NET Framework Veri Sağlayıcısı'nı kullanarak, bir veritabanı veya katalog şema işleme gerçekleştirmek için veri tanımlama dili ifadelerini (örneğin, CREATE TABLE ve ALTER COLUMN) ya da saklı yordamlar yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="72d4d-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="72d4d-104">Bu komutları bir sorgu olduğu gibi satır döndürmeyen böylece **komut** nesnesi sağlayan bir **ExecuteNonQuery** işlemek için.</span><span class="sxs-lookup"><span data-stu-id="72d4d-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="72d4d-105">Kullanmanın yanı sıra **ExecuteNonQuery** şemayı değiştirmek için de veri değiştirir, ancak değil, INSERT, UPDATE, gibi satırları döndürür ve silmek işlem SQL deyimleri için bu yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72d4d-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="72d4d-106">Satırları tarafından döndürülen değil ancak **ExecuteNonQuery** yöntemi, giriş ve çıkış parametrelerini ve dönüş değerlerini kullanılabilir geçirilen ve aracılığıyla döndürülen **parametreleri** koleksiyonunu **komutu**  nesne.</span><span class="sxs-lookup"><span data-stu-id="72d4d-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72d4d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="72d4d-107">In This Section</span></span>  
 [<span data-ttu-id="72d4d-108">Bir Veri Kaynağındaki Verileri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="72d4d-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="72d4d-109">Komutları ya da bir veritabanındaki verileri değiştirme saklı yordamları yürütme açıklar.</span><span class="sxs-lookup"><span data-stu-id="72d4d-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="72d4d-110">Katalog İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="72d4d-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="72d4d-111">Veritabanı şemasını değiştiren komutlar yürütmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="72d4d-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d4d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72d4d-112">See also</span></span>

- [<span data-ttu-id="72d4d-113">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="72d4d-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="72d4d-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="72d4d-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="72d4d-115">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="72d4d-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
