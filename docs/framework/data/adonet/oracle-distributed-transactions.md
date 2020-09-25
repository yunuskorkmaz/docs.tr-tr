---
title: Oracle Dağıtılmış İşlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a21134c3283d3d9d8d7660eecaaf74d60ecf6662
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166527"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="6f6ed-102">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="6f6ed-102">Oracle Distributed Transactions</span></span>

<span data-ttu-id="6f6ed-103"><xref:System.Data.OracleClient.OracleConnection>Nesne, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde otomatik olarak bunları listeler.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="6f6ed-104">Bağlantı bağlantı havuzundan açıldığında veya alındığında otomatik işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="6f6ed-105">Varolan işlemlerde otomatik kaydı devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="6f6ed-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="6f6ed-106">bir için bağlantı dizesi parametresi olarak <xref:System.Data.OracleClient.OracleConnection> .</span><span class="sxs-lookup"><span data-stu-id="6f6ed-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6ed-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-107">See also</span></span>

- [<span data-ttu-id="6f6ed-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f6ed-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="6f6ed-109">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f6ed-109">ADO.NET Overview</span></span>](ado-net-overview.md)
