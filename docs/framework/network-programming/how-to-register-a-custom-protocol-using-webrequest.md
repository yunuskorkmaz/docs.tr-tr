---
title: "Nasıl yapılır: WebRequest kullanarak özel bir protokolünü kaydetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="8c77c-102">Nasıl yapılır: WebRequest kullanarak özel bir protokolünü kaydetme</span><span class="sxs-lookup"><span data-stu-id="8c77c-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="8c77c-103">Bu örnek, belirli classthat başka bir yerde tanımlanan protokolünü kaydetme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8c77c-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="8c77c-104">Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **oluşturma** döndüren yöntem `CustomWebRequest` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8c77c-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="8c77c-105">Kod örneği, yazmıştır varsayar `CustomWebRequest` özel protokolü uygulayan kod.</span><span class="sxs-lookup"><span data-stu-id="8c77c-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c77c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c77c-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c77c-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8c77c-107">Compiling the Code</span></span>  
 <span data-ttu-id="8c77c-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8c77c-108">This example requires:</span></span>  
  
 <span data-ttu-id="8c77c-109">Başvurular <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8c77c-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c77c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c77c-110">See Also</span></span>  
 [<span data-ttu-id="8c77c-111">Programlama takılabilir protokolleri</span><span class="sxs-lookup"><span data-stu-id="8c77c-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
