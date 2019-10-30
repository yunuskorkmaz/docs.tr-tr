---
title: "Nasıl yapılır: bir WebRequest 'i Internet Ile Iletişim kurmak için proxy kullanmak üzere etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039547"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Nasıl yapılır: bir WebRequest 'i Internet Ile Iletişim kurmak için proxy kullanmak üzere etkinleştirme

Bu örnek, Internet ile iletişim kurmak için herhangi bir <xref:System.Net.WebRequest> proxy kullanmasını sağlayacak bir genel proxy örneği oluşturur. Örnek, proxy sunucusunun `webproxy` adlandırıldığı ve standart HTTP bağlantı noktası 80 bağlantı noktası üzerinden iletişim kurduğu varsayılmaktadır.

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

- C# **System.net** ad alanı için [`using` yönergesi](../../csharp/language-reference/keywords/using-directive.md) .
- **System.net** ad alanı için Visual Basic [`Imports` bir ifade](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
