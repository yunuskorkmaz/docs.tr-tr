---
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5c9a81fc61a2272056ba34fa387fdafee6203824
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079506"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="760db-102">Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme</span><span class="sxs-lookup"><span data-stu-id="760db-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="760db-103">Bu örnekte, başka yerde tanımlanmış bir protokolü belirli sınıf kaydettirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="760db-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="760db-104">Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **Oluştur** döndüren yöntem `CustomWebRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="760db-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="760db-105">Örnek kodu, yazmış varsayar `CustomWebRequest` özel protokolü uygulayan kodu.</span><span class="sxs-lookup"><span data-stu-id="760db-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="760db-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="760db-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="760db-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="760db-107">Compiling the Code</span></span>  
 <span data-ttu-id="760db-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="760db-108">This example requires:</span></span>  
  
 <span data-ttu-id="760db-109">Başvurular <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="760db-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="760db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="760db-110">See also</span></span>

- [<span data-ttu-id="760db-111">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="760db-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
