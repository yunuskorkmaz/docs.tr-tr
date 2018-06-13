---
title: 'Nasıl yapılır: WebRequest kullanarak özel bir protokolünü kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e6902adeac04d95d576ae72469624a5b4f8aa0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394598"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="f89bd-102">Nasıl yapılır: WebRequest kullanarak özel bir protokolünü kaydetme</span><span class="sxs-lookup"><span data-stu-id="f89bd-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="f89bd-103">Bu örnek, belirli classthat başka bir yerde tanımlanan protokolünü kaydetme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f89bd-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="f89bd-104">Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **oluşturma** döndüren yöntem `CustomWebRequest` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f89bd-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="f89bd-105">Kod örneği, yazmıştır varsayar `CustomWebRequest` özel protokolü uygulayan kod.</span><span class="sxs-lookup"><span data-stu-id="f89bd-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f89bd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f89bd-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f89bd-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f89bd-107">Compiling the Code</span></span>  
 <span data-ttu-id="f89bd-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f89bd-108">This example requires:</span></span>  
  
 <span data-ttu-id="f89bd-109">Başvurular <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f89bd-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89bd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f89bd-110">See Also</span></span>  
 [<span data-ttu-id="f89bd-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="f89bd-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
