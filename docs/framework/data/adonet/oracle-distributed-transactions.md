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
# <a name="oracle-distributed-transactions"></a>Oracle Dağıtılmış İşlemleri

<xref:System.Data.OracleClient.OracleConnection>Nesne, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde otomatik olarak bunları listeler. Bağlantı bağlantı havuzundan açıldığında veya alındığında otomatik işlem kaydı gerçekleşir. Varolan işlemlerde otomatik kaydı devre dışı bırakabilirsiniz  
  
```csharp  
Enlist=false  
```  
  
 bir için bağlantı dizesi parametresi olarak <xref:System.Data.OracleClient.OracleConnection> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
