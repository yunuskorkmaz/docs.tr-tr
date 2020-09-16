---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 736020695ae40a8884057ddee8aac8abe6e8c1fd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554201"
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
