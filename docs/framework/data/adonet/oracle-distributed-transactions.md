---
title: Oracle dağıtılmış işlemler
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 0e9dcb30eb1962071d7154d4bbf929871c8a12d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765207"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="2da86-102">Oracle dağıtılmış işlemler</span><span class="sxs-lookup"><span data-stu-id="2da86-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="2da86-103"><xref:System.Data.OracleClient.OracleConnection> Nesnesi bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2da86-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="2da86-104">Bağlantı açıldığında veya bağlantı havuzundan alınan otomatik işlem kaydı oluşur.</span><span class="sxs-lookup"><span data-stu-id="2da86-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="2da86-105">Belirterek otomatik kaydı varolan işlemlerde devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="2da86-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="2da86-106">için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="2da86-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da86-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2da86-107">See Also</span></span>  
 [<span data-ttu-id="2da86-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2da86-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="2da86-109">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2da86-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
