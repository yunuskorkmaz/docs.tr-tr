---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 9b31d93c1ebc0af9aa8e41b3a4c328af62da7e23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878337"
---
# <a name="clr-stored-procedures"></a>CLR Saklı Yordamları
Saklı yordamlar skaler ifadelerde kullanılamaz yordamlarını içindir. Tablo sonuçları ve iletileri istemciye döndürür, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimleri çağırabilir ve çıkış parametresi döndür.  
  
> [!NOTE]
>  Microsoft Visual Basic, Microsoft Visual C# yaptığı aynı şekilde çıkış parametreleri desteklemez. Parametre başvuruya göre geçirin ve uygulamak için belirtmelisiniz \<Out() > özniteliği aşağıdaki gibi bir çıktı parametresi temsil etmek için:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Sürümü, daha ayrıntılı bilgi için bkz. [SQL Server belgeleri](/sql) kullanmakta olduğunuz SQL Server sürümü için.
  
 **SQL Server belgeleri**

1. [CLR Saklı Yordamları](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodda SQL Server 2005 nesneleri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
