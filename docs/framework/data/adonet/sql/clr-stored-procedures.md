---
title: CLR saklı yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 1f8aa6fb9243706d07caa4527af0c4c880aa70a6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503117"
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda SQL Server 2005 nesneleri oluşturma](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
