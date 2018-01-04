---
title: "Nasıl yapılır: bir WebRequest eşleşen bir protokole özgü WebResponse alma"
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
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ef42c2cdc4d3b230195f89580a7c7abf0952f487
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Nasıl yapılır: bir WebRequest eşleşen bir protokole özgü WebResponse alma
Bu örnek bir WebRequest eşleşen bir protokole özgü WebResponse almak nasıl gösterir.  
  
## <a name="example"></a>Örnek  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular **System.Net** ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)
