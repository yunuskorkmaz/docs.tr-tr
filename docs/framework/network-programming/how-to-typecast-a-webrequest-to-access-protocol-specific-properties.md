---
title: 'Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: d38a40aa1e6e3db769aedfc440077721cdfaf06d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180749"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim
Bu örnek, protokole özgü özelliklere erişebilmeniz için Web İsteği'ni nasıl yazabileceğinizi gösterir.  
  
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
