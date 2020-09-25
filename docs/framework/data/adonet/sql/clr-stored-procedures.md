---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: aa14c96ed226ac80a9613d3e229f35dbf5085f3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173620"
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
