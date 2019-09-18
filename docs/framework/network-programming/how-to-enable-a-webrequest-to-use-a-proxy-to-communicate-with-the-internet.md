---
title: 'Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d569603fe22e5d8c8f59d21c2777c7c1bfcd531d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048291"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme
Bu örnek, Internet ile iletişim kurmak için bir proxy kullanmasını <xref:System.Net.WebRequest> sağlayacak küresel bir ara sunucu örneği oluşturur. Örnek, proxy sunucusunun adlandırıldığını `webproxy` ve standart http bağlantı noktası 80 bağlantı noktası üzerinden iletişim kurduğu varsayılmaktadır.  
  
## <a name="example"></a>Örnek  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- **System.net** ad alanı için bir [ `using` yönerge](../../csharp/language-reference/keywords/using-directive.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
