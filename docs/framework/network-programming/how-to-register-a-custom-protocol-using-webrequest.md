---
title: 'Nasıl yapılır: WebRequest kullanarak özel Protokolü kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1f78f98f94daa51c17a1294285e13dfddd457106
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244556"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="fc121-102">Nasıl yapılır: WebRequest kullanarak özel Protokolü kaydetme</span><span class="sxs-lookup"><span data-stu-id="fc121-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="fc121-103">Bu örnek, belirli classthat başka yerde tanımlanmış bir protokol kaydettirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc121-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="fc121-104">Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **Oluştur** döndüren yöntem `CustomWebRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="fc121-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="fc121-105">Örnek kodu, yazmış varsayar `CustomWebRequest` özel protokolü uygulayan kodu.</span><span class="sxs-lookup"><span data-stu-id="fc121-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc121-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc121-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc121-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fc121-107">Compiling the Code</span></span>  
 <span data-ttu-id="fc121-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fc121-108">This example requires:</span></span>  
  
 <span data-ttu-id="fc121-109">Başvurular <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fc121-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc121-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc121-110">See Also</span></span>  
 [<span data-ttu-id="fc121-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="fc121-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
