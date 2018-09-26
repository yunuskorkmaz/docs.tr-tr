---
title: 'Nasıl yapılır: protokole özgü özelliklere erişim WebRequest türü atayarak'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b4cde78ead9bdb8becf0f12497f4b37ad5a73bb3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085236"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="541dc-102">Nasıl yapılır: protokole özgü özelliklere erişim WebRequest türü atayarak</span><span class="sxs-lookup"><span data-stu-id="541dc-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="541dc-103">Bu örnekte, böylece protokole özgü özelliklere erişebilir WebRequest türü atayarak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="541dc-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="541dc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="541dc-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="541dc-105">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="541dc-105">See Also</span></span>  
 [<span data-ttu-id="541dc-106">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="541dc-106">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
