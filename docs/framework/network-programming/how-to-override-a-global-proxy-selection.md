---
title: "Nasıl yapılır: bir genel Proxy seçim geçersiz kıl"
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
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dc9f8f4e958d1988cecd769431e99d70ff2a4cfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-a-global-proxy-selection"></a>Nasıl yapılır: bir genel Proxy seçim geçersiz kıl
Bu örnek gönderir bir **WebRequest** genel proxy seçimi adlı bir proxy sunucusu ile geçersiz kılmaları www.contoso.com için `alternateproxy` bağlantı noktası 80 üzerinde.  
  
## <a name="example"></a>Örnek  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular **System.Net** ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama protokolleri kullanma](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Bir Proxy üzerinden Internet erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
