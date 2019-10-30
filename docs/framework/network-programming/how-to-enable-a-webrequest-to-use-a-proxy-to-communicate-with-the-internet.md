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
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="44de7-102">Nasıl yapılır: bir WebRequest 'i Internet Ile Iletişim kurmak için proxy kullanmak üzere etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="44de7-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="44de7-103">Bu örnek, Internet ile iletişim kurmak için herhangi bir <xref:System.Net.WebRequest> proxy kullanmasını sağlayacak bir genel proxy örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44de7-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="44de7-104">Örnek, proxy sunucusunun `webproxy` adlandırıldığı ve standart HTTP bağlantı noktası 80 bağlantı noktası üzerinden iletişim kurduğu varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44de7-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="44de7-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="44de7-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="44de7-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="44de7-106">Compiling the Code</span></span>

<span data-ttu-id="44de7-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="44de7-107">This example requires:</span></span>

- <span data-ttu-id="44de7-108">C# **System.net** ad alanı için [`using` yönergesi](../../csharp/language-reference/keywords/using-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="44de7-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="44de7-109">**System.net** ad alanı için Visual Basic [`Imports` bir ifade](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) .</span><span class="sxs-lookup"><span data-stu-id="44de7-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="44de7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44de7-110">See also</span></span>

- [<span data-ttu-id="44de7-111">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="44de7-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="44de7-112">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="44de7-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
