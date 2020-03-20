---
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048258"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="613e7-102">Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme</span><span class="sxs-lookup"><span data-stu-id="613e7-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="613e7-103">Bu örnek, başka bir yerde tanımlanan bir protokol belirli sınıf nasıl kaydolun gösterir.</span><span class="sxs-lookup"><span data-stu-id="613e7-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="613e7-104">Bu örnekte, `CustomWebRequestCreator` `CustomWebRequest` nesneyi döndüren **Oluşturma** yöntemini uygulayan kullanıcı tarafından uygulanan nesnedir.</span><span class="sxs-lookup"><span data-stu-id="613e7-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="613e7-105">Kod örneği, özel protokolü uygulayan `CustomWebRequest` kodu yazdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="613e7-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="613e7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="613e7-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="613e7-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="613e7-107">Compiling the Code</span></span>  
 <span data-ttu-id="613e7-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="613e7-108">This example requires:</span></span>  
  
 <span data-ttu-id="613e7-109"><xref:System.Net> Ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="613e7-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="613e7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="613e7-110">See also</span></span>

- [<span data-ttu-id="613e7-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="613e7-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
