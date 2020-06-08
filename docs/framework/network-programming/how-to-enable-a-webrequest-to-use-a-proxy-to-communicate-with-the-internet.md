---
title: 'Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme'
description: Web Isteklerini .NET Framework internet ile iletişim kurmak üzere bir proxy kullanmasını sağlamak için genel bir proxy örneği oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502541"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme

Bu örnek <xref:System.Net.WebRequest> , Internet ile iletişim kurmak için bir proxy kullanmasını sağlayacak küresel bir ara sunucu örneği oluşturur. Örnek, proxy sunucusunun adlandırıldığını `webproxy` ve standart http bağlantı noktası 80 bağlantı noktası üzerinden iletişim kurduğu varsayılmaktadır.

## <a name="example"></a>Örnek

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a>Kod Derleniyor

Bu örnek şunları gerektirir:

- **System.net** ad alanı için C# [ `using` yönergesi](../../csharp/language-reference/keywords/using-directive.md) .
- **System.net** ad alanı için Visual Basic bir [ `Imports` ifade](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
