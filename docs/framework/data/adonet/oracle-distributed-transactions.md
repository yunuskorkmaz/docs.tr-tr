---
title: Oracle Dağıtılmış İşlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: edd06b94ce4157e90d334ee7feac2a449f7ee74b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040474"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="5e857-102">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="5e857-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="5e857-103"><xref:System.Data.OracleClient.OracleConnection> nesnesi, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde otomatik olarak listeler.</span><span class="sxs-lookup"><span data-stu-id="5e857-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="5e857-104">Bağlantı bağlantı havuzundan açıldığında veya alındığında otomatik işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5e857-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="5e857-105">Varolan işlemlerde otomatik kaydı devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="5e857-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="5e857-106">bir <xref:System.Data.OracleClient.OracleConnection>için bağlantı dizesi parametresi olarak.</span><span class="sxs-lookup"><span data-stu-id="5e857-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e857-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e857-107">See also</span></span>

- [<span data-ttu-id="5e857-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5e857-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="5e857-109">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e857-109">ADO.NET Overview</span></span>](ado-net-overview.md)
