---
title: "Oracle dağıtılmış işlemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c901ccf9132dc766d78efb24428b6469458a70fa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="81184-102">Oracle dağıtılmış işlemler</span><span class="sxs-lookup"><span data-stu-id="81184-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="81184-103"><xref:System.Data.OracleClient.OracleConnection> Nesnesi bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="81184-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="81184-104">Bağlantı açıldığında veya bağlantı havuzundan alınan otomatik işlem kaydı oluşur.</span><span class="sxs-lookup"><span data-stu-id="81184-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="81184-105">Belirterek otomatik kaydı varolan işlemlerde devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="81184-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="81184-106">için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="81184-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81184-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81184-107">See Also</span></span>  
 [<span data-ttu-id="81184-108">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81184-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="81184-109">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="81184-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
