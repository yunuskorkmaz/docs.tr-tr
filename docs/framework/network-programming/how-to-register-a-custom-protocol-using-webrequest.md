---
title: 'Nasıl yapılır: WebRequest kullanarak özel Protokolü kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5f863aa61058e87a7911bab3b02c3ba345419596
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193610"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="66e7d-102">Nasıl yapılır: WebRequest kullanarak özel Protokolü kaydetme</span><span class="sxs-lookup"><span data-stu-id="66e7d-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="66e7d-103">Bu örnek, belirli classthat başka yerde tanımlanmış bir protokol kaydettirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66e7d-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="66e7d-104">Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **Oluştur** döndüren yöntem `CustomWebRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="66e7d-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="66e7d-105">Örnek kodu, yazmış varsayar `CustomWebRequest` özel protokolü uygulayan kodu.</span><span class="sxs-lookup"><span data-stu-id="66e7d-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66e7d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e7d-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66e7d-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="66e7d-107">Compiling the Code</span></span>  
 <span data-ttu-id="66e7d-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="66e7d-108">This example requires:</span></span>  
  
 <span data-ttu-id="66e7d-109">Başvurular <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="66e7d-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e7d-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66e7d-110">See Also</span></span>  
 [<span data-ttu-id="66e7d-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="66e7d-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
