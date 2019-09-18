---
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048258"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="43579-102">Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme</span><span class="sxs-lookup"><span data-stu-id="43579-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="43579-103">Bu örnek, başka bir yerde tanımlanan protokole özgü bir sınıfın nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="43579-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="43579-104">Bu örnekte, `CustomWebRequestCreator` `CustomWebRequest` nesnesini döndüren **Create** yöntemini uygulayan kullanıcı tarafından uygulanan nesnedir.</span><span class="sxs-lookup"><span data-stu-id="43579-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="43579-105">Kod örneği, özel protokolü uygulayan `CustomWebRequest` kodu yazdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="43579-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43579-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="43579-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43579-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="43579-107">Compiling the Code</span></span>  
 <span data-ttu-id="43579-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="43579-108">This example requires:</span></span>  
  
 <span data-ttu-id="43579-109"><xref:System.Net> Ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="43579-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43579-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43579-110">See also</span></span>

- [<span data-ttu-id="43579-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="43579-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
