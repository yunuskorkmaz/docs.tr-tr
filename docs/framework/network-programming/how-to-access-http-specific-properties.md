---
title: 'Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 107e57ca947012f5e2f65835d684f5e6068b3681
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642743"
---
# <a name="how-to-access-http-specific-properties"></a>Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim
Bu örnek HTTP devre dışı bırakma gösterir **tutma** davranışı ve get protokol sürümü, Web sunucusu vm'sinden sayı.  
  
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
 Bu örnek gerektirir:  
  
- Başvurular **System.Net** ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
- [HTTP](../../../docs/framework/network-programming/http.md)
