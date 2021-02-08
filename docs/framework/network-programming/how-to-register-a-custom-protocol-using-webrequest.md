---
description: 'Daha fazla bilgi edinin: nasıl yapılır: WebRequest kullanarak özel protokol kaydetme'
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 7415017f20c0c6ed80570992e249fb8121907de2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785763"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="1ca2c-103">Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme</span><span class="sxs-lookup"><span data-stu-id="1ca2c-103">How to: Register a Custom Protocol Using WebRequest</span></span>

<span data-ttu-id="1ca2c-104">Bu örnek, başka bir yerde tanımlanan protokole özgü bir sınıfın nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ca2c-104">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="1ca2c-105">Bu örnekte, `CustomWebRequestCreator` nesnesini döndüren **Create** yöntemini uygulayan kullanıcı tarafından uygulanan nesnedir `CustomWebRequest` .</span><span class="sxs-lookup"><span data-stu-id="1ca2c-105">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="1ca2c-106">Kod örneği, `CustomWebRequest` özel protokolü uygulayan kodu yazdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="1ca2c-106">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ca2c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ca2c-107">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1ca2c-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1ca2c-108">Compiling the Code</span></span>  

 <span data-ttu-id="1ca2c-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1ca2c-109">This example requires:</span></span>  
  
 <span data-ttu-id="1ca2c-110"><xref:System.Net>Ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="1ca2c-110">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca2c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ca2c-111">See also</span></span>

- [<span data-ttu-id="1ca2c-112">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="1ca2c-112">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
