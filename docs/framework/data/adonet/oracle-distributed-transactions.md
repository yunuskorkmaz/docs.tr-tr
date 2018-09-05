---
title: Oracle dağıtılmış işlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a3b8a50b42b945a0cdc1cbfbc4cc9eab835e90e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505405"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="b820e-102">Oracle dağıtılmış işlemleri</span><span class="sxs-lookup"><span data-stu-id="b820e-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="b820e-103"><xref:System.Data.OracleClient.OracleConnection> Nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b820e-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="b820e-104">Bağlantı açılamıyor veya bağlantı havuzundan alınan otomatik bir işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="b820e-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="b820e-105">Belirterek mevcut işlemlerde otomatik kayıt devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b820e-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="b820e-106">için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="b820e-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b820e-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b820e-107">See Also</span></span>  
 [<span data-ttu-id="b820e-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b820e-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="b820e-109">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b820e-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
