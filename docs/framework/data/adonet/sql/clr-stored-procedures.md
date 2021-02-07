---
description: 'Daha fazla bilgi edinin: CLR saklı yordamları'
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d136d3dcb12be2f87276a410c9fa0e713b7dfd52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723627"
---
# <a name="clr-stored-procedures"></a>CLR Saklı Yordamları

Saklı yordamlar, skalar ifadelerde kullanılamayan yordamlardır. Bunlar istemciye tablo sonuçları ve iletileri döndürebilir, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimlerini çağırabilir ve çıkış parametrelerini döndürebilir.  
  
> [!NOTE]
> Microsoft Visual Basic, çıkış parametrelerini Microsoft Visual C# ' nin desteklediği şekilde desteklemez. Parametreyi başvuruya göre geçirmek ve \<Out()> aşağıdaki gibi bir çıkış parametresini temsil etmek için özniteliğini uygulamak için belirtmelisiniz:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için [SQL Server belgelerine](/sql) bakın.
  
 **SQL Server belgeleri**

1. [CLR Saklı Yordamları](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodda SQL Server 2005 nesneleri oluşturma](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
