---
description: 'Daha fazla bilgi edinin: Oracle dağıtılmış Işlemler'
title: Oracle Dağıtılmış İşlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: d0c41920f18e0f56ebdf57e3cb82cf829a59c450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786179"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="a39b1-103">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="a39b1-103">Oracle Distributed Transactions</span></span>

<span data-ttu-id="a39b1-104"><xref:System.Data.OracleClient.OracleConnection>Nesne, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde otomatik olarak bunları listeler.</span><span class="sxs-lookup"><span data-stu-id="a39b1-104">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="a39b1-105">Bağlantı bağlantı havuzundan açıldığında veya alındığında otomatik işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a39b1-105">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="a39b1-106">Varolan işlemlerde otomatik kaydı devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="a39b1-106">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="a39b1-107">bir için bağlantı dizesi parametresi olarak <xref:System.Data.OracleClient.OracleConnection> .</span><span class="sxs-lookup"><span data-stu-id="a39b1-107">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39b1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a39b1-108">See also</span></span>

- [<span data-ttu-id="a39b1-109">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a39b1-109">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="a39b1-110">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a39b1-110">ADO.NET Overview</span></span>](ado-net-overview.md)
