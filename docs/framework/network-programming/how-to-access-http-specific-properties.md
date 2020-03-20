---
title: 'Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 68ad6b2c55cd5cc467e53441caa778ea10b994fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180861"
---
# <a name="how-to-access-http-specific-properties"></a>Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim
Bu örnek, HTTP Canlı **Tutma** davranışını nasıl kapatAcaklarını ve Web sunucusundan protokol sürüm numarasını nasıl alacağımı gösterir.  
  
## <a name="example"></a>Örnek  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- **System.Net** ad alanına başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [HTTP Kı.,](http.md)
