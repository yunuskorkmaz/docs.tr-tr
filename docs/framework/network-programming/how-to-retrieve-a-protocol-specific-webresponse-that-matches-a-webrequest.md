---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
description: .NET Framework bir WebRequest ile eşleşen protokole özgü bir WebResponse almayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fd163c115dcd19c05f93f4c202b043440834ba9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266746"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma

Bu örnek, WebRequest ile eşleşen protokole özgü bir WebResponse 'un nasıl alınacağını gösterir.  
  
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

 Bu örnek şunları gerektirir:  
  
- **System.net** ad alanına başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri İsteme](requesting-data.md)
