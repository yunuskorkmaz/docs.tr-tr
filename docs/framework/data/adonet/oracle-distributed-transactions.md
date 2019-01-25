---
title: Oracle dağıtılmış işlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 8e7530621254881402570b59b47a22052b40f2b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713260"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="d4718-102">Oracle dağıtılmış işlemleri</span><span class="sxs-lookup"><span data-stu-id="d4718-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="d4718-103"><xref:System.Data.OracleClient.OracleConnection> Nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d4718-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="d4718-104">Bağlantı açılamıyor veya bağlantı havuzundan alınan otomatik bir işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d4718-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="d4718-105">Belirterek mevcut işlemlerde otomatik kayıt devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="d4718-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="d4718-106">için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="d4718-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4718-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4718-107">See also</span></span>
- [<span data-ttu-id="d4718-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d4718-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="d4718-109">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d4718-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
