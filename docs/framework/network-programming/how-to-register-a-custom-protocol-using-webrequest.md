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
ms.workload: dotnet
ms.openlocfilehash: 7fefaf65fe0bf1c761e976359f3015389a557369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
