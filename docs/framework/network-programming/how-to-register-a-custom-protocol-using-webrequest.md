---
title: "Nasıl yapılır: WebRequest kullanarak özel bir protokolünü kaydetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Nasıl yapılır: WebRequest kullanarak özel bir protokolünü kaydetme
Bu örnek, belirli classthat başka bir yerde tanımlanan protokolünü kaydetme gösterilmektedir. Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **oluşturma** döndüren yöntem `CustomWebRequest` nesnesi. Kod örneği, yazmıştır varsayar `CustomWebRequest` özel protokolü uygulayan kod.  
  
## <a name="example"></a>Örnek  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
 Başvurular <xref:System.Net> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama takılabilir protokolleri](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
