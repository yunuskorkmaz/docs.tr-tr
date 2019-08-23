---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c02efa3f0a91d176b626761335bd2d5a2b96b966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917951"
---
# <a name="clr-stored-procedures"></a>CLR Saklı Yordamları
Saklı yordamlar, skalar ifadelerde kullanılamayan yordamlardır. Bunlar istemciye tablo sonuçları ve iletileri döndürebilir, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimlerini çağırabilir ve çıkış parametrelerini döndürebilir.  
  
> [!NOTE]
> Microsoft Visual Basic, çıkış parametrelerini Microsoft görsele C# aynı şekilde desteklemez. Parametreyi başvuruya göre geçirmek ve \<çıkış parametresini göstermek için out () > özniteliğini aşağıda gösterildiği gibi belirtmeniz gerekir:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için [SQL Server belgelerine](/sql) bakın.
  
 **SQL Server belgeleri**

1. [CLR Saklı Yordamları](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodda SQL Server 2005 nesneleri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
