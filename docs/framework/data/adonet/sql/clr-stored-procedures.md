---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: ca0fd2d33f0ad56c96fb63530e6ba3f7f7890f81
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450368"
---
# <a name="clr-stored-procedures"></a>CLR Saklı Yordamları
Saklı yordamlar, skalar ifadelerde kullanılamayan yordamlardır. Bunlar istemciye tablo sonuçları ve iletileri döndürebilir, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimlerini çağırabilir ve çıkış parametrelerini döndürebilir.  
  
> [!NOTE]
> Microsoft Visual Basic, çıkış parametrelerini Microsoft görsele C# aynı şekilde desteklemez. Parametreyi başvuruya göre geçirmek ve aşağıdaki gibi bir çıkış parametresini temsil etmek için \<Out () > özniteliğini uygulamanız gerekir:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için [SQL Server belgelerine](/sql) bakın.
  
 **SQL Server belgeleri**

1. [CLR Saklı Yordamları](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodda SQL Server 2005 nesneleri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
