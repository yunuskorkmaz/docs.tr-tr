---
title: 'Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: 09bd551dad77358b1503871c6ee100a869adf75b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253433"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim

Bu örnek, protokole özgü özelliklere erişebilmek için bir WebRequest 'in nasıl ekleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
  
```csharp  
HttpWebRequest httpreq =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)
