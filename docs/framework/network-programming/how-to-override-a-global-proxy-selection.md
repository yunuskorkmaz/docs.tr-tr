---
title: 'Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma'
description: Bir URL 'ye Web Isteği göndererek genel proxy seçimini geçersiz kılmak için bu örneği izleyin. Bu, seçimi bir ara sunucu ile geçersiz kılar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502515"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma
Bu örnek **WebRequest** `www.contoso.com` , genel proxy seçimini, `alternateproxy` bağlantı noktası 80 ' de adlı bir ara sunucu Ile geçersiz kılacak bir Web isteği gönderir.  
  
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
 Bu örnek şunları gerektirir:  
  
- **System.net** ad alanı için bir [ `using` yönerge](../../csharp/language-reference/keywords/using-directive.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
