---
title: Oracle Dağıtılmış İşlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795152"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="06d13-102">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="06d13-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="06d13-103"><xref:System.Data.OracleClient.OracleConnection> Nesne, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde otomatik olarak bunları listeler.</span><span class="sxs-lookup"><span data-stu-id="06d13-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="06d13-104">Bağlantı bağlantı havuzundan açıldığında veya alındığında otomatik işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="06d13-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="06d13-105">Varolan işlemlerde otomatik kaydı devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="06d13-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="06d13-106">bir için <xref:System.Data.OracleClient.OracleConnection>bağlantı dizesi parametresi olarak.</span><span class="sxs-lookup"><span data-stu-id="06d13-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d13-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06d13-107">See also</span></span>

- [<span data-ttu-id="06d13-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="06d13-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="06d13-109">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="06d13-109">ADO.NET Overview</span></span>](ado-net-overview.md)
