---
title: CLR saklı yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: a1a37ac1257594913c6d06cb08df2882e8773da8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554640"
---
# <a name="clr-stored-procedures"></a>CLR saklı yordamları
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
- [Yönetilen kodda SQL Server 2005 nesneleri oluşturma](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
