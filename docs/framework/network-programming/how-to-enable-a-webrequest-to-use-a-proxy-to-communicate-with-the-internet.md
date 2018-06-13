---
title: 'Nasıl yapılır: Internet ile iletişim kurmak için bir proxy sunucu kullanmak bir WebRequest etkinleştir'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0f57869dfecce3e59d0a255a6201dd966bc407e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396912"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="4d41e-102">Nasıl yapılır: Internet ile iletişim kurmak için bir proxy sunucu kullanmak bir WebRequest etkinleştir</span><span class="sxs-lookup"><span data-stu-id="4d41e-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="4d41e-103">Bu örnek herhangi etkinleştirecek bir genel proxy örneği oluşturur <xref:System.Net.WebRequest> Internet ile iletişim kurmak için bir proxy sunucu kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="4d41e-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="4d41e-104">Örnek proxy sunucusu adlandırıldığını varsayar `webproxy` ve onu iletişim kurar, bağlantı noktası 80, standart HTTP bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="4d41e-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d41e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d41e-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d41e-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4d41e-106">Compiling the Code</span></span>  
 <span data-ttu-id="4d41e-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4d41e-107">This example requires:</span></span>  
  
-   <span data-ttu-id="4d41e-108">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4d41e-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d41e-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d41e-109">See Also</span></span>  
 [<span data-ttu-id="4d41e-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="4d41e-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="4d41e-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="4d41e-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
