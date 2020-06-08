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
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="a2829-103">Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a2829-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="a2829-104">Bu örnek <xref:System.Net.WebRequest> , Internet ile iletişim kurmak için bir proxy kullanmasını sağlayacak küresel bir ara sunucu örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2829-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="a2829-105">Örnek, proxy sunucusunun adlandırıldığını `webproxy` ve standart http bağlantı noktası 80 bağlantı noktası üzerinden iletişim kurduğu varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2829-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="a2829-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2829-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="a2829-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a2829-107">Compiling the Code</span></span>

<span data-ttu-id="a2829-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a2829-108">This example requires:</span></span>

- <span data-ttu-id="a2829-109">**System.net** ad alanı için C# [ `using` yönergesi](../../csharp/language-reference/keywords/using-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="a2829-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="a2829-110">**System.net** ad alanı için Visual Basic bir [ `Imports` ifade](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) .</span><span class="sxs-lookup"><span data-stu-id="a2829-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2829-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2829-111">See also</span></span>

- [<span data-ttu-id="a2829-112">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2829-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="a2829-113">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="a2829-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
