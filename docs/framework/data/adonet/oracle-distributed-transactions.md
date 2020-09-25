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
# <a name="oracle-distributed-transactions"></a>Oracle Dağıtılmış İşlemleri

<xref:System.Data.OracleClient.OracleConnection>Nesne, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde otomatik olarak bunları listeler. Bağlantı bağlantı havuzundan açıldığında veya alındığında otomatik işlem kaydı gerçekleşir. Varolan işlemlerde otomatik kaydı devre dışı bırakabilirsiniz  
  
```csharp  
Enlist=false  
```  
  
 bir için bağlantı dizesi parametresi olarak <xref:System.Data.OracleClient.OracleConnection> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
