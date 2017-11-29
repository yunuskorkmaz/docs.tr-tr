---
title: "Verileri değiştirmek için komutları kullanarak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 853f8e4e75df3fffad4a2d5ecd4f7ae21b5d674f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="6d2d7-102">Verileri değiştirmek için komutları kullanarak</span><span class="sxs-lookup"><span data-stu-id="6d2d7-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="6d2d7-103">Bir .NET Framework veri sağlayıcısı kullanarak, saklı yordamları ya da bir veritabanı veya katalog şema işleme gerçekleştirmek için veri tanımlama dili ifadelerini (örneğin, CREATE TABLE ve ALTER COLUMN) yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="6d2d7-104">Sorguda yaptığınız gibi bu komutları satır döndürmeyen böylece **komutu** nesnesi sağlar bir **ExecuteNonQuery** işlemek için.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="6d2d7-105">Kullanmanın yanı sıra **ExecuteNonQuery** şemayı değiştirmek için de veri değiştirir, ancak değil INSERT, UPDATE gibi satırları döndürür ve silme işlemini SQL deyimleri için bu yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="6d2d7-106">Satır tarafından döndürülmez rağmen **ExecuteNonQuery** yöntemi, giriş ve çıkış parametreler ve dönüş değerleri kullanılabilir geçirilen ve aracılığıyla döndürülen **parametreleri** koleksiyonu **komutu**  nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d2d7-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6d2d7-107">In This Section</span></span>  
 [<span data-ttu-id="6d2d7-108">Bir veri kaynağındaki verileri güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6d2d7-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="6d2d7-109">Komutları ya da bir veritabanındaki verileri değiştirme saklı yordamları çalıştırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="6d2d7-110">Katalog işlemlerini gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6d2d7-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="6d2d7-111">Veritabanı şeması değiştirme komutları yürütmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2d7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2d7-112">See Also</span></span>  
 [<span data-ttu-id="6d2d7-113">Alma ve ADO.NET veri değiştirme</span><span class="sxs-lookup"><span data-stu-id="6d2d7-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="6d2d7-114">Komutları ve parametreleri</span><span class="sxs-lookup"><span data-stu-id="6d2d7-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="6d2d7-115">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6d2d7-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
