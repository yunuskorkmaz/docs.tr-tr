---
title: Oracle Dağıtılmış İşlemleri
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 4af1c98818f1929850c5ae78892c64993a93d4d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771962"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="b1556-102">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b1556-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="b1556-103"><xref:System.Data.OracleClient.OracleConnection> Nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b1556-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="b1556-104">Bağlantı açılamıyor veya bağlantı havuzundan alınan otomatik bir işlem kaydı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="b1556-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="b1556-105">Belirterek mevcut işlemlerde otomatik kayıt devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b1556-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="b1556-106">için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="b1556-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1556-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1556-107">See also</span></span>

- [<span data-ttu-id="b1556-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b1556-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="b1556-109">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b1556-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
