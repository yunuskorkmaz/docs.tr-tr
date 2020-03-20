---
title: 'Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039547"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme

Bu örnek, Herhangi <xref:System.Net.WebRequest> bir Internet ile iletişim kurmak için bir proxy kullanmak sağlayacak genel bir proxy örneği oluşturur. Örnek, proxy sunucusunun adlandırılmış `webproxy` olduğunu ve standart HTTP bağlantı noktası olan 80 bağlantı noktasında iletişim kurduğunu varsayar.

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

- **System.Net** ad alanı için bir C# [ `using` yönergesi.](../../csharp/language-reference/keywords/using-directive.md)
- System.Net ad alanı için **Görsel** Temel [ `Imports` ifadesi.](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
