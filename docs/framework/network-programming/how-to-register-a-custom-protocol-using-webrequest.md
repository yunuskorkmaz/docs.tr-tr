---
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5c9a81fc61a2272056ba34fa387fdafee6203824
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642561"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="de945-102">Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme</span><span class="sxs-lookup"><span data-stu-id="de945-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="de945-103">Bu örnekte, başka yerde tanımlanmış bir protokolü belirli sınıf kaydettirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="de945-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="de945-104">Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **Oluştur** döndüren yöntem `CustomWebRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="de945-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="de945-105">Örnek kodu, yazmış varsayar `CustomWebRequest` özel protokolü uygulayan kodu.</span><span class="sxs-lookup"><span data-stu-id="de945-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de945-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="de945-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de945-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="de945-107">Compiling the Code</span></span>  
 <span data-ttu-id="de945-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="de945-108">This example requires:</span></span>  
  
 <span data-ttu-id="de945-109">Başvurular <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="de945-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de945-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de945-110">See also</span></span>

- [<span data-ttu-id="de945-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="de945-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
